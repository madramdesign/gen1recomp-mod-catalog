# Discovered mods (GitHub + Reddit)

Research · **August 2, 2026**  
Install status updated after bulk install into live mods + app mirror.

---

## Verdict

| Source | Result |
| --- | --- |
| **Official index** | [bryanthaboi/gen1recomp-mod-index](https://github.com/bryanthaboi/gen1recomp-mod-index) — **29** published mods |
| **GitHub search** | Extra high-signal repos beyond the index also installed where a release/source zip existed |
| **Reddit** | **No usable hits** — community hub is **Discord** ([bois.icu](https://bois.icu)) |
| **Installed now** | **56** mod folders on disk (see `INSTALLED-MODS.md`). Only **`DRAMATIC_SHAPE`** is enabled |

---

## Install batch (Aug 2, 2026)

Copied into both:

- `~/Library/Application Support/pokemon-love2d/mods/<id>/`
- `/Applications/gen1recomp.app/mods/<id>/`

All new ids set to `false` in `options.lua` (missing key = enabled by default).

### Official index — installed

All 29 index entries are on disk (`DRAMATIC_SHAPE`, `nuzlocke`, plus the previous “not installed” 27).

### Extra GitHub finds — installed

| id (folder) | Source repo |
| --- | --- |
| `overworld_wild_spawns` | YoDrehDenSwagAuf/overworld-spawn-mod |
| `gen1recomp_ds` | BartInTheField/gen1recomp-ds-mod (source tag zip) |
| `crystal_animated_sprites_with_shiny_visuals` | distilledorion-sketch/… |
| `Gold_Silver_Sprites` | OtaconRevengeance/gold_sprites |
| `erilab_bottomless_bag` | erereck/gen1recomp-bottomless-bag |
| `erilab_bag_wrap` | erereck/gen1recomp-bag-wrap |
| `mash-catch` | mresnick67/Gen1ReComp-ButtonMash |
| `choose_your_hero` | TranswarpTechnologies/choose-your-hero-mod-gen1recomp |
| `mew_under_truck` | Windwrecker/Mew-Under-the-Truck |
| `anytime_rename` | Roxas2712/pokemon-gen1-recomp-mod-anytime-rename |
| `unified_pc_move` | blazor67/Unified-PC-Move (source tag zip) |
| `Gen_5_6_7_Cries` | Lachie123456/Stadium-Cries (Gen 5–7 cry pack asset) |

### Not pulled (tools / ports / thin signal)

Translation generators, handheld/engine ports, and zero-star speculative repos from the research note were skipped. Re-check Discord + the mod index for new releases.

---

## Overlap warning vs local customs

| Local mod | Public alternative |
| --- | --- |
| `pc_anywhere` | `ACCESS_PC_ANYWHERE` |
| `walk_behind` | `FOLLOWERS_EX` |
| `modern_pc_boxes` | `gen3_box` / `unified_pc_move` |
| `red_blue_qol` | `quality_of_life` + `running_shoes` + `bag_999` |
| `higher_framerate` | Built-in Options MAX FPS |

Don’t stack both sides of a row at once.

---

## Suggested enable order

1. Keep **DRAMATIC_SHAPE** (already on) if you want the voxel look  
2. Add one QoL pack: `quality_of_life` **or** keep local `red_blue_qol` — not both  
3. Optional UX: `useful_dex`, `battle_move_info` / `MOVE_MATCHUP`, `surround_audio`  
4. Challenge: `nuzlocke` **or** `pokemon_randomizer`  
5. Heavy content (`modern_kanto`, `gen1online`, sprite packs): enable alone, restart, test

Full inventory: `INSTALLED-MODS.md`.

---

*Sources: GitHub release pages + jsdelivr mirror of bryanthaboi/gen1recomp-mod-index `mods/*/meta.json`.*
