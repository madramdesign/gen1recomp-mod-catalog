# gen1recomp modding notes

Living notes from building mods against the packaged macOS app and the
[project wiki](https://github.com/bryanthaboi/gen1recomp/wiki).

Engine: **1.0.0** · mod API: **2** · identity: `pokemon-love2d`

---

## Install locations

| Place | Path | Survives app updates? |
| --- | --- | --- |
| **Save-dir mods (preferred)** | `~/Library/Application Support/pokemon-love2d/mods/<id>/` | Yes |
| Inside `.app` | Usually **not** usable (fused `game.love`) | No / signed |
| Portable copy | e.g. `~/Downloads/<mod_id>/` | Manual reinstall |

Packaged macOS uses identity `pokemon-love2d` **without** a `LOVE/` segment
(see wiki Getting Started). Source checkouts use the same identity under
`~/Library/Application Support/LOVE/pokemon-love2d/` when run via `love .`.

### Minimal mod layout

```
mods/my_mod/
├── manifest.json
└── main.lua
```

**No zip required** for local play. Zip only for sharing (`modkit pack` /
in-game import).

`manifest.json` example:

```json
{
  "id": "my_mod",
  "name": "My Mod",
  "version": "1.0.0",
  "entry": "main.lua",
  "api": 2
}
```

`api: 2` → strict schema (`did you mean "baseStats"?`). Content changes need
a **restart** (registries freeze after boot). Options/hooks/events can apply
live when they only touch runtime state.

Enable/disable: Options → Mods. Persists in `options.lua`
(`options.mods[id] = false` means disabled; missing means enabled).

---

## Core concepts

### Registries (data)

37 content registries. Verbs: `register`, `override`, `patch`, `remove`,
`get`, `each`.

- `patch` deep-merges records; **arrays replace wholesale** unless wrapped
  with `{ __append = { ... } }` / `__prepend`.
- Record fields are **camelCase** from the importer (`baseStats`, not
  `base_stats`).

### Events (notify)

`mod.events:on(name, fn)`. Payloads usually read-only.

Important mutable event:

- `pokemon.before_give` → `{ ctx, species, level, nickname? }`  
  Every story gift / `give_pokemon` passes through; rewrite `species` /
  `level` / `nickname` before the mon is built.

Other useful events: `game.ready`, `save.created`, `save.loaded`,
`map.entered`, `mod.options_changed`, `battle.*`, intro oak speech events.

### Hooks (intercept)

`mod.hooks:wrap(name, function(next, ...) ... end)`. Call `next` at most once.

Useful hooks: `trainer.party`, `battle.damage`, `encounter.roll`,
`movement.speed`, `ui.options.rows`, `ui.start_menu.items`,
`script.command`, `intro.oak_speech.build`.

### Map scripts

`mod.content.map_scripts:register("MAP_ID", { talk = { TEXT_FOO = ... } })`

Talk entries can be:

1. **Row lists** `{ { "show_text", "..." }, ... }`
2. **Functions** `function(game, ow, npc, onDone)` — best for dynamic logic

Per TEXT constant: highest-precedence contribution wins. Prefer **label**
jumps over absolute row numbers.

Function handlers should run rows via:

```lua
ow.runner:run(rows, {
  npc = npc,
  onDone = onDone or function() end,
  source = { modId = mod.id, strict = true, mapId = "OAKS_LAB", hook = "talk" },
})
```

### Persistence

| API | Backing store | Use for |
| --- | --- | --- |
| `mod.save:get/set` | `save.modData[modId]` | Per-save progress |
| `mod.options:define/get` | `options.modOptions[modId]` | Settings (survive New Game) |

Option row types: `toggle`, `choice`, `number`, `text`.

### Custom script commands

```lua
mod.commands:register("my_cmd", function(ctx, ...) end)
-- then in a script row: { "my_cmd", arg1, arg2 }
```

### Permissions / requires

Without declaring permissions, mods may only `require`:

- `src.mods.Semver`
- `src.audio.ChipAsm`
- `src.pokemon.Stats`

`engine_internals` / `network` / `filesystem` must be listed in the
manifest if needed. Prefer the `mod` facade + `game` from `game.ready`
over requiring engine modules.

### Platform rules

- Vanilla with no mods == parity oracle
- Broken mods are isolated; disable restores vanilla
- **No ROM bytes in mods** (no IPS/BPS; use asset transforms)
- v1 mods keep working under API 2

---

## Clocks: FPS vs game speed (important)

| Setting | Option key | Module | What it does |
| --- | --- | --- | --- |
| **MAX FPS** | `options.fpsCap` | `src/core/FrameCap.lua` | Render present cap only |
| **GAME SPEED** | `options.speed` | `src/core/GameSpeed.lua` | Logic fast-forward |

- Logic is **fixed-step ~60Hz** (`FixedStep.lua`). Raising FPS does **not**
  make walk/battle/text faster by itself.
- Valid FPS steps: `30, 40, 50, 60, 75, 90, 100, 120, 144, 160` (default 60).
- Valid speeds: `1, 2, 4, 10, 20, 30, 50, 75, 100, 200` (default 1).
- Audio does **not** pitch-shift with speed.
- `conf.lua` sets `vsync = 1`. If vsync holds the display to 60Hz, a higher
  `fpsCap` mostly no-ops until vsync is forced off by the driver/OS.
- Vanilla Options already has **MAX FPS** and **GAME SPEED** rows.

Mod pattern used by `higher_framerate`:

```lua
mod.events:on("game.ready", function(ev)
  local opts = ev.game.save.options
  opts.fpsCap = 120
  opts.speed = 1
  ev.game:applyOptions(opts)
  ev.game:writeOptions()
end)
```

---

## Oak's Lab starters

Vanilla script: `data/scripts/oaks_lab.lua`

- Balls (objects): Charmander (6,3), Squirtle (7,3), Bulbasaur (8,3)
- Flow: DexEntry → ask → received text → `give_pokemon` → flags → rival
  takes counterpick ball
- Chose flags: `EVENT_CHOSE_CHARMANDER` / `_SQUIRTLE` / `_BULBASAUR`
- Rival parties indexed from those flags (`Commands.rival_battle`, lab
  `onStep` uses `start_battle` with party 1/2/3)
- Classic starter species in rival parties (and evolutions) can be rewritten
  with the `trainer.party` hook

`random_starters` approach:

1. Roll a trio into `mod.save` on `save.created` / first `OAKS_LAB` enter
2. Replace the three ball talk scripts with functions that inject the rolled
   species into dex/ask/give/rival text
3. `trainer.party` swaps classic starter-line slots for the counterpick
   species, evolved along `LEVEL` methods to the slot level

---

## Installed mods (this machine)

| id | Path | Purpose |
| --- | --- | --- |
| `random_starters` | `.../mods/random_starters/` | Random Oak's Lab starters |
| `higher_framerate` | `.../mods/higher_framerate/` | Auto-raise MAX FPS (+ optional speed) |
| `red_blue_qol` | `.../mods/red_blue_qol/` | Community most-wanted Gen 1 QoL pack |
| `modern_pc_boxes` | `.../mods/modern_pc_boxes/` | Modern PC: 32×30 grid, grab-and-move |
| `walk_behind` | `.../mods/walk_behind/` | Lead Pokemon follows behind you |
| `pc_anywhere` | `.../mods/pc_anywhere/` | Start-menu PC from anywhere |

Portable copies also live under `~/Downloads/<id>/`.

---

## PC anywhere

`OverworldState:openPC` builds the Center PC menu (Bill's / item / Oak).
`ui.start_menu.items` can insert a row that calls `game.overworld:openPC()`.

---

## Walk-behind Pokemon

Yellow already ships a full follower (`src/world/PikachuFollower.lua`): trail
queue, idle bounces, ledge hops, talk emotions. Spawn is gated by
`GameVersion.isYellow()` + `SPRITE_PIKACHU` + party Pikachu.

`walk_behind` patches the local `shouldSpawn` / `makeFollower` upvalues via
`debug.setupvalue` (needs `engine_internals`) so Red/Blue get the same trail
behavior for the **first healthy party mon**.

Sprite limitation: Red’s OW sheet has no per-species walk cycles. Mapping:

- species specials (Snorlax, Seel line, Clefairy…, Pikachu if Yellow sheet)
- else primary type → SEEL / BIRD / FAIRY / MONSTER

Talk: Yellow+Pikachu keeps native emotions; otherwise cry + “happy to see you”.

Soft-lock risk: wrapping `PF.update` every frame (sprite refresh / re-spawn)
can leave the overworld stuck while the window still redraws. Keep refresh on
map enter only; default the mod / option **off** until proven stable.

---

## Modern PC boxes

Vanilla Bill's PC: **12 boxes × 20**, list menus, save confirm on box change
(`src/pokemon/Boxes.lua`, `src/ui/BoxMenu.lua`).

`Boxes.COUNT` / `Boxes.CAPACITY` are hardcoded (same bagSize issue) — expanding
needs `engine_internals` + growing `save.boxes` in `ensure`.

`mod.content.screens:register("BoxMenu", …)` replaces Bill's PC UI (builtin is
require-fallback; not pre-registered in Builtins).

Modern UX in `modern_pc_boxes`:

- 32 boxes × 30 slots (6×5 grid), party strip on top
- A grab / place / swap; hold while changing boxes
- Up to header, Left/Right change box (also wrap at grid edges)
- START summary, SELECT jump party↔box, SELECT+B release
- B cancel grab or save+exit

---

## Community most-wanted Red/Blue QoL (research)

Sources reviewed (Jul 2026):

- [Shin Pokemon / shinpokered](https://github.com/jojobear13/shinpokered) — bugfixes + QoL remaster
- [PureRGB](https://github.com/Vortyne/pureRGB) — optional QoL toggles, near-vanilla
- [Yume / yumepokered](https://github.com/PokefanMarcel/yumepokered) — enhancement hack QoL list
- [red-qol](https://github.com/rellimn/red-qol) — toggleable small enhancements
- [Beyond RB](https://github.com/Sandingo/beyondrb), [Solus RGB](https://github.com/Dechrissen/poke-solus-rgb)
- Romhacking.net Shin Blue/Red feature lists

### Consensus ranking (near-vanilla players)

1. **Running shoes** (hold B) — universal #1
2. **Reusable / repurchaseable TMs**
3. **Trade evolutions without trading** (Kadabra, Machoke, Graveler, Haunter)
4. **Engine quirk fixes** (1/256 miss, Focus Energy, etc.) — gen1recomp already ships `modern_clean`
5. **Bigger bag** / key-item pocket
6. **HM field-move QoL** (use without sacrificing a moveslot) — harder; not in `red_blue_qol` v1
7. Repel reuse prompt, EXP bar, Select=bike/rod — also common; deferred

### How `red_blue_qol` maps them

| Feature | Mechanism |
| --- | --- |
| Running shoes | `movement.speed` hook (Cookbook R40) |
| Run while surfing | same hook + `ctx.surfing` |
| Reusable TMs | patch each `TM_*` `machine.kind` → `"HM"` so ItemEffects returns `learnkept` |
| Trade evos | `evolution.check` hook: TRADE methods also fire on `levelup` ≥ option level (default 37) |
| Modern rules | set `options.ruleset = "modern_clean"` on `game.ready` |
| 40-slot bag | `require("src.inventory.Bag").CAPACITY = 40` + `constants:patch("bagSize", 40)` — needs `engine_internals` because Bag ignores `constants.bagSize` today |
| Fast text | `options.textSpeed = 1` |
| Bag scroll | `ui.list_menu` wrap/pageJump/keyRepeat for `kind == "bag"` |

**Caveats**

- Reusable TM teach text may say “Booted up an HM!” (kind check); moves remain forgettable.
- `reusable_tms` / `bigger_bag` need **restart** after toggling.
- HM-without-moveslot and EXP bar need deeper UI work — not in v1.

---

## Wiki map (bookmark)

- [Home](https://github.com/bryanthaboi/gen1recomp/wiki)
- [Getting Started](https://github.com/bryanthaboi/gen1recomp/wiki/Getting-Started)
- [Concepts: Events and Hooks](https://github.com/bryanthaboi/gen1recomp/wiki/Concepts-Events-And-Hooks)
- [Concepts: Registries](https://github.com/bryanthaboi/gen1recomp/wiki/Concepts-Registries)
- [Reference: Events](https://github.com/bryanthaboi/gen1recomp/wiki/Reference-Events)
- [Reference: Hooks](https://github.com/bryanthaboi/gen1recomp/wiki/Reference-Hooks)
- [Reference: Mod Object](https://github.com/bryanthaboi/gen1recomp/wiki/Reference-Mod-Object)
- [Cookbook](https://github.com/bryanthaboi/gen1recomp/wiki/Cookbook)

Repo pointer in tree: `docs/modding.md` → wiki.

---

## Unpacking the app for research

```bash
mkdir -p /tmp/gen1recomp_love
cd /tmp/gen1recomp_love
unzip -o -q "/path/to/gen1recomp.app/Contents/Resources/game.love"
```

Useful paths inside the love archive:

- `src/mods/` — loader, schemas, runtime
- `src/core/FrameCap.lua`, `GameSpeed.lua`, `FixedStep.lua`
- `data/scripts/oaks_lab.lua` — starter balls
- `src/script/Commands.lua` — `give_pokemon`, `rival_battle`

ROM cache / generated data (player machine):

`~/Library/Application Support/pokemon-love2d/data/generated/`
