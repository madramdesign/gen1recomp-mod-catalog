# Master feature list — DO NOT RECREATE

**Source of truth** for work already done on this Gen1Recomp install.  
Before scaffolding a new mod, search this file. Prefer **enabling / extending** an existing mod over writing a duplicate.

Updated: **August 2, 2026**

| Also see | Role |
| --- | --- |
| `INSTALLED-MODS.md` | Disk inventory + enable flags |
| `MOD-IDEAS.md` | Future ideas (check here first — “Already covered”) |
| `DISCOVERED-MODS.md` | Where public mods were found |
| `BEST-MODS.md` / `LEARNINGS.md` | Research notes |

**Our GitHub:**  
[madramdesign/gen1recomp-battle-exp-bar](https://github.com/madramdesign/gen1recomp-battle-exp-bar) · [madramdesign/gen1recomp-professor-oak-challenge](https://github.com/madramdesign/gen1recomp-professor-oak-challenge)

---

## Built by us (this machine / madramdesign)

| Feature | Mod id | Notes |
| --- | --- | --- |
| Gen 3+ battle EXP bar | `battle_exp_bar` | Blue/black/off; classic + wide. Do **not** also enable QoL’s BATTLE EXP BAR |
| Professor Oak Challenge | `professor_oak_challenge` | Mewlax RB order (Brock→Misty→Koga→Erika); soft/hard gates; Start checklist; **area catch HUD** |
| POC area “NEED HERE” overlay | *(same)* | On map enter / always option |
| POC guide tips in checklist | *(same)* | From Mewlax RB Oak Guide |
| Extra research docs | `Extra/*.md` | BEST-MODS, DISCOVERED, MOD-IDEAS, LEARNINGS, this file |

---

## Features by category (installed mods)

### Challenge / run modes

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Nuzlocke (permadeath, 1/area, etc.) | `nuzlocke` | ✓ |
| Professor Oak Challenge | `professor_oak_challenge` | ✓ |
| Full randomizer | `pokemon_randomizer` | ✓ |
| Random Oak starters | `random_starters` | ✓ |
| Yellow Legacy balance / trade→level | `yellow_legacy_changes` | ✓ |
| Modern rules / phys-spec split pack | `modern_kanto` | ✓ (beta) |

### Overworld gameplay

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Visible / reactive wild Pokémon | `overworld_wild_spawns` | ✓ |
| Hold/toggle run (shoes) | `RUN_MODE`, `running_shoes`, `red_blue_qol` | pick **one** |
| Lead / pack followers | `FOLLOWERS_EX`, `walk_behind` | pick **one** (`walk_behind` soft-lock risk) |
| Heal from Start menu | `HEAL_ANYWHERE` | ✓ |
| PC from Start menu | `ACCESS_PC_ANYWHERE`, `pc_anywhere` | pick **one** |
| Trainer rematches | `trainer_rematch` | ✓ |
| Real-world step EXP (mobile) | `pokewalker` | ✓ |
| Mew under Vermilion truck | `mew_under_truck` | ✓ |
| Button-mash catch | `mash-catch` | ✓ |

### Battle UI / info

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| EXP bar under HP | `battle_exp_bar`, `quality_of_life` | pick **one** EXP implementation |
| Type matchup / move power on select | `MOVE_MATCHUP`, `battle_move_info` | overlapping — don’t ship a third |
| Caught indicator in battle | `quality_of_life` | ✓ |
| Widescreen battle intro flash | `widescreen_battle_intro` | ✓ |
| Weather damage ruleset demo | `example_weather` | gallery only |

### Dex / menus / PC

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Dex stats / moves pages | `useful_dex` | ✓ |
| DexNav-style overlay | `example_dexnav` | gallery; extend or fork, don’t clone |
| Gen 3–style box UI (12×20) | `gen3_box` | ✓ |
| Expanded modern PC (32×30) | `modern_pc_boxes` | ✓ — soft-lock risk if stacked |
| Unified withdraw/deposit/swap PC | `unified_pc_move` | ✓ |
| Anytime rename trainer/party | `anytime_rename` | ✓ |
| Multi save slots | `MULTI_SAVE_SLOTS` | ✓ |

### Bag / inventory

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Bigger bag (40 / 255 / 999) | `red_blue_qol`, `erilab_bottomless_bag`, `bag_999` | pick **one** |
| Bag wrap / circular cursor | `erilab_bag_wrap`, `red_blue_qol` | overlapping |
| Bag sort | `bag_999` | ✓ |
| Reusable TMs | `red_blue_qol` | ✓ |
| Trade evo on level-up (QoL) | `red_blue_qol`, `yellow_legacy_changes` | overlapping |

### Visuals / audio

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Voxel 3D overworld / 3D battles | `DRAMATIC_SHAPE` | ✓ |
| Crystal animated + shiny battle sprites | `crystal_animated_sprites_with_shiny_visuals` | ✓ — don’t stack with GS sprites |
| Gold/Silver battle sprites | `Gold_Silver_Sprites` | ✓ — conflicts with Crystal pack |
| Shiny colors / sparkles (battle + OW) | `SHINY_POKEMON`, crystal pack | overlapping sparkles OK to tune, don’t rewrite |
| Dual-screen DS layout | `gen1recomp_ds` | ✓ |
| Stereo / 5.1 audio | `surround_audio` | ✓ |
| In-game music player | `MUSIC_PLAYER` | ✓ |
| Jukebox / ChipAsm demo | `example_jukebox` | gallery |
| Gen 5–7 cry pack | `Gen_5_6_7_Cries` | ✓ |
| Player recolor demo | `example_shiny_palette` | gallery |
| Controller rumble | `CONTROLLER_RUMBLE` | ✓ |

### Avatar / story / content

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Girl / Leaf avatar | `leaf_avatar`, `choose_your_hero` | overlapping |
| Booker's Heaven quest | `bookers_heaven` | ✓ |
| Fetch-quest demo | `example_lost_parcel` | gallery |
| Silly Oak intro | `example_silly_oak` | gallery |
| Mew starter demo | `example_mew_starter` | gallery |
| Mini total conversion | `example_mini_conversion` | gallery |
| Balance tweak demo | `example_balance_tweaks` | gallery |

### Online / meta

| Feature | Mod id(s) | Do not rebuild |
| --- | --- | --- |
| Online multiplayer / GTS | `gen1online` | ✓ |
| PT-BR translation | `versaovermelha` | ✓ |
| Dutch translation | `translation-nl` | ✓ |

### Engine options (built-in — not mods)

| Feature | Where | Do not rebuild as a mod |
| --- | --- | --- |
| MAX FPS / GAME SPEED / text speed | Options | `higher_framerate` is mostly redundant |
| `modern_clean` / `gen1_faithful` rulesets | Options → Ruleset | ✓ |
| Colors, tilt, zoom, GBC FX, void fill | Options / hotkeys | ✓ |
| Performance tier | Options | ✓ |
| Mod manager import/enable | F10 | ✓ |

### Bundled QoL packs (feature umbrellas)

| Pack | Includes (approx.) | Conflict warning |
| --- | --- | --- |
| `quality_of_life` | EXP bar, caught indicator, location banners, easy interactions | vs `battle_exp_bar`, vs stacking with heavy packs |
| `red_blue_qol` | Run, reusable TMs, trade-on-level, bag 40, fast text, modern_clean | vs `running_shoes` / `RUN_MODE` / `bag_*` / QoL |

---

## Overlap matrix (never enable both)

| A | B | Why |
| --- | --- | --- |
| `battle_exp_bar` | QoL **BATTLE EXP BAR** | Same HUD |
| `pc_anywhere` | `ACCESS_PC_ANYWHERE` | Same Start→PC |
| `walk_behind` | `FOLLOWERS_EX` | Same follower role |
| `modern_pc_boxes` | `gen3_box` / `unified_pc_move` | Competing PC UIs |
| `red_blue_qol` | `quality_of_life` + run/bag mods | Stacked QoL |
| `running_shoes` | `RUN_MODE` | Same movement hook |
| `bag_999` | `erilab_bottomless_bag` | Bag capacity |
| `Gold_Silver_Sprites` | `crystal_animated_sprites_with_shiny_visuals` | Battle sprite replace |
| `leaf_avatar` | `choose_your_hero` | Protagonist select |
| `MOVE_MATCHUP` | `battle_move_info` | Move-select info |
| `nuzlocke` | custom nuzlocke fork | One challenge ruleset |
| `professor_oak_challenge` | another POC mod | One checklist/gate |

---

## EXP.ALL / Exp Share

| Feature | Status |
| --- | --- |
| Vanilla **EXP.ALL** item | Built into Gen 1 (Route 15 Aide) — not a mod |
| Always-on / Gen-6-style party Exp Share | **Not researched as an existing mod** — OK to build |
| Battle EXP **bar** | Already done (`battle_exp_bar` / QoL) — different feature |
| Step → party EXP | `pokewalker` — different feature |

---

## Still open (OK to build) — see `MOD-IDEAS.md`

Examples **not** on this machine as a dedicated mod yet:

- HM Tools (field HMs without moveslot)  
- Town Map / full Area Dex wild data  
- Repel reuse prompt  
- Move Deleter / Reminder NPCs  
- Daycare Egg / Living Dex tracker  
- IronMon ruleset  
- Level caps  
- Phone / Match Call lite  

If an idea appears both here and in MOD-IDEAS “Already covered”, **this file wins**.

---

## Checklist before new work

1. Ctrl+F this file for the feature name.  
2. Check `INSTALLED-MODS.md` for an existing id.  
3. If it exists: enable, configure, or **extend** that mod — don’t start `my_exp_bar_2`.  
4. If building anyway: document why (bugfix, different design) and add a row here when shipped.

---

*Update this file whenever a mod is added, merged, or retired.*
