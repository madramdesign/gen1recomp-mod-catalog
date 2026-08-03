# Installed mods

All **56** mods below are present on disk. Enable individually via **F10** / Start → Mods,
then restart for content changes. Missing `options.mods.<id>` = enabled by default;
this inventory sets unknown/new mods to **`false`** until you opt in.

| Path | Location |
| --- | --- |
| Live (game loads) | `~/Library/Application Support/pokemon-love2d/mods/<id>/` |
| Portable mirror | `/Applications/gen1recomp.app/mods/<id>/` |
| Enable flags | `~/Library/Application Support/pokemon-love2d/options.lua` |

## Showcase / big features

| id | Name | Version | Status |
| --- | --- | --- | --- |
| `bookers_heaven` | Booker's Heaven | 1.1.0 | Disabled |
| `DRAMATIC_SHAPE` | Dramatic Shape Voxel Mod | 1.5.2 | Disabled |
| `gen1online` | Gen1Online | 0.2.1 | Disabled |
| `gen1recomp_ds` | Dual Screen (DS-style) | 2026.8.1+2 | Disabled |
| `leaf_avatar` | Choose Your Avatar | 1.2.0 | Disabled |
| `modern_kanto` | Modern Kanto | 0.2.0 | Disabled |
| `nuzlocke` | Nuzlocke | 1.0.1 | Disabled |
| `overworld_wild_spawns` | Wilds of Kanto | 0.6.0 | Enabled |
| `battle_exp_bar` | Battle EXP Bar | 1.0.0 | Enabled |
| `professor_oak_challenge` | Professor Oak Challenge | 0.1.0 | Enabled |
| `pokemon_randomizer` | Pokémon Gen 1 Randomizer | 0.46.1 | Disabled |
| `pokewalker` | Pokewalker (Step Sync) | 0.3.2 | Disabled |
| `quality_of_life` | Quality of Life from later generations | 1.2.2 | Disabled |

## Official index — QoL / UI

| id | Name | Version | Status |
| --- | --- | --- | --- |
| `ACCESS_PC_ANYWHERE` | Access PC Anywhere | 1.0.1 | Disabled |
| `bag_999` | 999 Bag Slots | 1.1.0 | Disabled |
| `battle_move_info` | Battle Move Info | 1.1.2 | Disabled |
| `CONTROLLER_RUMBLE` | Controller Rumble | 1.0.3 | Disabled |
| `FOLLOWERS_EX` | Followers EX | 1.0.2 | Disabled |
| `gen3_box` | Gen 3 Box | 1.3.0 | Disabled |
| `HEAL_ANYWHERE` | Heal Anywhere | 1.0.0 | Disabled |
| `MOVE_MATCHUP` | Battle Move Info | 1.0.7 | Disabled |
| `MULTI_SAVE_SLOTS` | Multiple Save Slots | 1.0.0 | Disabled |
| `MUSIC_PLAYER` | Music Player | 1.2.5 | Disabled |
| `RUN_MODE` | Run Mode | 1.2.0 | Disabled |
| `running_shoes` | Running Shoes | 1.1.0 | Disabled |
| `SHINY_POKEMON` | Shiny Pokemon | 1.0.1 | Enabled |
| `surround_audio` | Stereo & 5.1 Audio | 1.6.0 | Disabled |
| `trainer_rematch` | Trainer Rematch | 0.4.2 | Disabled |
| `useful_dex` | Useful Dex | 1.2.1 | Disabled |
| `widescreen_battle_intro` | Widescreen Battle Intro | 1.3.0 | Disabled |
| `yellow_legacy_changes` | Yellow Legacy Changes | 1.9.0 | Disabled |

## Translations

| id | Name | Version | Status |
| --- | --- | --- | --- |
| `translation-nl` | Dutch translation | 0.0.2 | Disabled |
| `versaovermelha` | VersãoVermelha | 0.2.0 | Disabled |

## Extra GitHub finds

| id | Name | Version | Status |
| --- | --- | --- | --- |
| `anytime_rename` | Anytime Rename | 1.1.1 | Disabled |
| `choose_your_hero` | Choose Your Hero | 0.1.1 | Disabled |
| `crystal_animated_sprites_with_shiny_visuals` | Crystal Animated Sprites with Shiny Visuals | 1.0.0 | Enabled |
| `erilab_bag_wrap` | EriLab Bag Wrap | 1.0.0 | Disabled |
| `erilab_bottomless_bag` | EriLab Bottomless Bag | 1.1.0 | Disabled |
| `Gen_5_6_7_Cries` | Gen_5_6_7_Cries | 1.2 | Disabled |
| `Gold_Silver_Sprites` | Pokémon Gold & Silver Sprites | 1.0.1 | Disabled |
| `mash-catch` | Mash Catch | 0.1.0 | Disabled |
| `mew_under_truck` | Mew Under the Truck | 1.4.0 | Disabled |
| `unified_pc_move` | Unified PC Move | 1.1.0 | Disabled |

## Local / custom

| id | Name | Version | Status |
| --- | --- | --- | --- |
| `higher_framerate` | Higher Framerate | 1.0.0 | Disabled |
| `modern_pc_boxes` | Modern PC Boxes | 1.0.0 | Disabled |
| `pc_anywhere` | PC Anywhere | 1.0.0 | Disabled |
| `random_starters` | Random Starters | 1.0.0 | Disabled |
| `red_blue_qol` | Red/Blue QoL Pack | 1.0.0 | Disabled |
| `walk_behind` | Walk Behind Pokemon | 1.0.0 | Disabled |

## Official examples

| id | Name | Version | Status |
| --- | --- | --- | --- |
| `example_balance_tweaks` | Balance Tweaks Example | 1.0.0 | Disabled |
| `example_dexnav` | DexNav Example | 1.0.0 | Disabled |
| `example_jukebox` | Jukebox Example | 1.0.0 | Disabled |
| `example_lost_parcel` | The Lost Parcel | 1.0.0 | Disabled |
| `example_mew_starter` | Mew Starter Example | 1.0.0 | Disabled |
| `example_mini_conversion` | Sable Cove (Mini Conversion) | 1.0.0 | Disabled |
| `example_shiny_palette` | Shiny Palette Example | 1.0.0 | Disabled |
| `example_silly_oak` | Silly Oak Intro Example | 1.0.0 | Disabled |
| `example_weather` | Weather Battles Example | 1.0.0 | Disabled |

---

## Notes

- Currently enabled: **overworld_wild_spawns** + **battle_exp_bar** + **professor_oak_challenge** + **crystal_animated_sprites_with_shiny_visuals** + **SHINY_POKEMON**. Game speed ×2, text Fast, MAX FPS 120.
- Do not stack overlapping QoL (e.g. `pc_anywhere` + `ACCESS_PC_ANYWHERE`, `walk_behind` + `FOLLOWERS_EX`, `red_blue_qol` + `quality_of_life` / `running_shoes` / `bag_999`).
- `Gen_5_6_7_Cries` came from the Stadium-Cries repo’s Gen 5–7 cry pack (that repo’s available release assets).
- Soft-lock risk mods (`walk_behind`, heavy UI like PC overhauls): enable one at a time and test.

See also: `FEATURES-DONE.md` (**do not recreate**), `BEST-MODS.md`, `DISCOVERED-MODS.md`, `LEARNINGS.md`, `MOD-IDEAS.md`.
