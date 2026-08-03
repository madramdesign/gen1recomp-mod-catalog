# Best mods for Gen1Recomp (pokemon-love2d)

Research notes · **August 2, 2026**  
Engine identity: `pokemon-love2d` · Mod API: **2**  
Official sources only: [bryanthaboi/gen1recomp](https://github.com/bryanthaboi/gen1recomp) · [Wiki](https://github.com/bryanthaboi/gen1recomp/wiki) · [Discord](https://bois.icu)

> **Do not use `gen1recomp.com`.** The project explicitly warns that site is not affiliated and should not be trusted for downloads.

---

## Quick start: how to install a mod

1. Prefer a **GitHub Release `.zip`** (files at archive root with `manifest.json` + `main.lua`).
2. In-game: **F10** (or Start → Mods) → **Import mod .zip**.
3. Or copy the folder into the save-dir mods root (survives app updates):

| OS | Mods path |
| --- | --- |
| macOS (packaged app) | `~/Library/Application Support/pokemon-love2d/mods/<id>/` |
| macOS (`love .` from source) | `~/Library/Application Support/LOVE/pokemon-love2d/mods/<id>/` |
| Windows | `%APPDATA%\love\pokemon-love2d\mods\` (or without `love\` on some builds) |
| Linux | `~/.local/share/love/pokemon-love2d/mods/` |

4. Enable in the mod manager. **Content** changes need a **restart**. Hooks/options can apply live.
5. Missing from `options.mods` = **enabled by default**. Set `options.mods.<id> = false` to disable.

Mods must **not** ship ROM bytes — only recipes / original assets / transforms that rebuild from your imported cache.

---

## Tier list (player-facing)

### S — Must-try community / official gameplay

| Mod | Why it’s “best” | Get it |
| --- | --- | --- |
| **Dramatic Shape Voxel Mod** (`DRAMATIC_SHAPE`) | The flagship visual mod: voxel diorama overworld, optional 3D battles, water reflections, day/night, tilt-shift, AA, experimental 1ST-person + **PC VR** (OpenXR). Presentational only (`affects_link: false`). ~700★ on GitHub; widely covered by press. | [Releases](https://github.com/DramaticShape/DramaticShapeVoxelMod/releases) — latest researched: **v1.5.2** (`DRAMATIC_SHAPE-1.5.2.zip`). Needs gen1recomp **≥ 0.1.37** (see manifest `game_version`). |
| **Nuzlocke** (`nuzlocke`) | Official challenge mod: Slow Start config via Oak, nicknames, 1 catch/area, no dupe families, permanent death, wipe save on whiteout. Configurable, maintained as its own repo with auto-releases. | [bryanthaboi/nuzlocke](https://github.com/bryanthaboi/nuzlocke) · [v1.0.1 zip](https://github.com/bryanthaboi/nuzlocke/releases/tag/v1.0.1). Also mirrored under `mods/nuzlocke` in the engine tree. |

### A — Built into the game (no mod required)

These are often what players want first; they ship in Options and beat most “QoL mods” for stability.

| Feature | Where | Notes |
| --- | --- | --- |
| **MAX FPS** / **GAME SPEED** | Options | Logic stays 60 Hz; FPS is present-rate only. Speed multiplies logic steps. |
| **`modern_clean` ruleset** | Options → Ruleset | Fixes 1/256 miss, Focus Energy bug, enemy PP, Hyper Beam recharge, etc. Faithful default is `gen1_faithful`. |
| **COLORS / TILT / ZOOM / GBC FX / VOID FILL** | Options + hotkeys `2`–`5` | Presentation; Voxel mod remaps some hotkeys but Options rows remain. |
| **Performance tier** | Options → Performance | HIGH / BALANCED / LOW / AUTO for weak hardware. |
| **Mod manager** | F10 | Import, enable, per-mod options, errors. |

### A — Official example gallery (copy up one level to load)

Shipped in the repo under [`mods/examples/`](https://github.com/bryanthaboi/gen1recomp/tree/main/mods/examples) so they **do not** auto-load (parity). Copy one to `mods/<id>/` to try.

| id | Persona | What you get |
| --- | --- | --- |
| `example_balance_tweaks` | Tweaker | Faster starters, cheaper TMs, Route 1 re-slot |
| `example_shiny_palette` | Artist | Teal player recolor via **asset transforms** (legal cache recipe) |
| `example_jukebox` | Musician | ChipAsm song, cry, jukebox screen (`engine_internals`) |
| `example_lost_parcel` | Quest author | Two-town fetch quest on vanilla NPCs |
| `example_weather` | Mechanic | Rain ruleset that scales Water/Fire via `battle.damage` |
| `example_dexnav` | Tool builder | Start-menu Dex overlay + inter-mod `exports` API |
| `example_mini_conversion` | TC team | “Sable Cove” mini total conversion |
| `example_silly_oak` | Intro author | Extra Oak questions / sprite swaps / `mod.save` answers |
| `example_mew_starter` | Legacy (api 1) | Oak’s Charmander → L20 Mew (compat proof) |

Gallery README: [mods/examples/README.md](https://github.com/bryanthaboi/gen1recomp/blob/main/mods/examples/README.md).

### B — Cookbook “best QoL” recipes (DIY, small & stable)

From the [Cookbook](https://github.com/bryanthaboi/gen1recomp/wiki/Cookbook). These are the community consensus QoL patterns (also common in Shin / PureRGB / red-qol ROM hacks), implemented the official way:

| Recipe | Feature |
| --- | --- |
| **R40** | Running shoes (hold B) — `movement.speed` |
| **R38** | Gen-2-like ruleset toggles (or just use built-in `modern_clean`) |
| **R45** | Bag wrap / page-jump / hold-scroll — `ui.list_menu` |
| **R31** | Custom Start-menu row — `ui.start_menu.items` |
| **R41** | Day/night palettes — `world.tod` + `map.palette` |
| **R39** | Shiny battle indicator |
| **R48** | Super Game Boy border |
| **R43** | CD-quality map music (file override) |

Full ladder if you want to *author* mods: [Tutorials 01–12](https://github.com/bryanthaboi/gen1recomp/wiki/Tutorials).

---

## Recommended play stacks

### 1. Vanilla+ (safest)

- No third-party mods
- Options: `modern_clean`, MAX FPS 60–120, text speed Fast
- Optional: copy **one** example (`example_balance_tweaks` *or* `example_dexnav`)

### 2. Showcase / “wow” run

- **Dramatic Shape Voxel Mod** only (or + Nuzlocke if you want pain)
- Keep Performance tier sensible on handhelds; AA is expensive (default OFF)
- Update gen1recomp first so `game_version` matches the voxel release

### 3. Challenge run

- **Nuzlocke** alone first (learn Soft Start options at Oak)
- Add Voxel later if you want the look without stacking unknown QoL mods

### 4. Near-vanilla QoL (DIY or local)

Prefer cookbook R40 + built-in ruleset over large untested packs. If you use local packs (see below), enable **one at a time**.

---

## Local / custom mods on this machine

Previously built under Application Support; as of late Jul 2026 they were moved to `mods/_disabled/` after soft-lock reports. Treat as **experimental**, not “best”:

| id | Intent | Status / risk |
| --- | --- | --- |
| `red_blue_qol` | Running shoes, reusable TMs, trade evos on level-up, bigger bag, fast text | Useful ideas; needs re-validation after freeze episode |
| `higher_framerate` | Auto-set fpsCap / speed | Mostly redundant with Options |
| `modern_pc_boxes` | 32×30 PC + grid UI | Powerful; complex UI = soft-lock risk |
| `pc_anywhere` | Start → PC | Simple; verify Start menu pop order |
| `walk_behind` | Lead mon follower (Yellow engine on Red) | **Known soft-lock risk** — leave off |
| `random_starters` | Random Oak lab trio | Content-only; relatively safe |

Restoring: move a folder from `mods/_disabled/<id>` back to `mods/<id>`, enable one, restart, test 10+ minutes before stacking.

Portable copies may also exist under `~/Downloads/<id>/`.

---

## Where to find more mods

| Source | Role |
| --- | --- |
| [Official Discord](https://bois.icu) | Announcements + community mod sharing (primary hub) |
| [GitHub Releases](https://github.com/bryanthaboi/gen1recomp/releases) | Engine only — not a mod store |
| Mod repos with `"github": "owner/repo"` in manifest | In-game Update / Versions when published correctly |
| [Guide: Publishing](https://github.com/bryanthaboi/gen1recomp/wiki/Guide-Publishing) | How authors ship `.zip` / `.modpkg` |
| [DramaticShape/DramaticShapeVoxelMod](https://github.com/DramaticShape/DramaticShapeVoxelMod) | Largest public third-party mod |
| [bryanthaboi/nuzlocke](https://github.com/bryanthaboi/nuzlocke) | Official challenge mod standalone |

As of this research date, **public GitHub search** shows few other standalone gen1recomp mod repos beyond Voxel + Nuzlocke + the in-tree examples. Expect most new mods to appear on **Discord** first.

---

## Stability & stacking rules

1. **One big mod at a time** when testing (especially anything with `engine_internals`).
2. Voxel + Nuzlocke is a known “showcase + challenge” combo; both are maintained.
3. Prefer Options / Cookbook hooks over patches that rewrite `src.*` via `debug` / `require`.
4. Soft-locks often look like a freeze while the window still redraws — force-quit, disable the last mod, restart.
5. After freezes, check `options.lua` wasn’t rewritten by a live session with old enable flags.
6. Link play: content/overhaul mods may change the link fingerprint (`affects_link`). Voxel is marked presentational-only.

---

## Tools for authors

| Tool | Link |
| --- | --- |
| Modkit CLI (`scaffold` / `validate` / `pack`) | [Guide Modkit](https://github.com/bryanthaboi/gen1recomp/wiki/Guide-Modkit) |
| Tiled map editor build | [bryanthaboi/tiled_gen1recomp](https://github.com/bryanthaboi/tiled_gen1recomp/releases) |
| Registry / hooks reference | [Wiki Reference](https://github.com/bryanthaboi/gen1recomp/wiki) |
| Local notes | `LEARNINGS.md` beside this file |

---

## Sources consulted

- [gen1recomp README](https://github.com/bryanthaboi/gen1recomp/blob/main/README.md) (official Discord, fake-site warning, rulesets, Options)
- [Wiki Home](https://github.com/bryanthaboi/gen1recomp/wiki), [Getting Started](https://github.com/bryanthaboi/gen1recomp/wiki/Getting-Started), [Cookbook](https://github.com/bryanthaboi/gen1recomp/wiki/Cookbook), [Publishing](https://github.com/bryanthaboi/gen1recomp/wiki/Guide-Publishing)
- [mods/examples/README.md](https://github.com/bryanthaboi/gen1recomp/blob/main/mods/examples/README.md) + per-mod manifests
- [DramaticShapeVoxelMod](https://github.com/DramaticShape/DramaticShapeVoxelMod) README + manifest + release **v1.5.2**
- [bryanthaboi/nuzlocke](https://github.com/bryanthaboi/nuzlocke) README + release **v1.0.1**
- Press: [80.lv voxel article](https://80.lv/articles/play-pok-mon-red-blue-yellow-in-voxel-world-without-emulation), [RetroDodo install guide](https://retrododo.com/how-to-download-pokemon-red-blue-3d-mod/)
- Local `LEARNINGS.md` (QoL consensus from Shin / PureRGB / red-qol / Beyond RB, and soft-lock notes)

---

*Living doc — refresh release tags and Discord pins periodically; this ecosystem moves fast.*
