# Cool mod ideas for Gen1Recomp

Research notes · **August 2, 2026**  
For Pokémon Red/Blue/Yellow on [gen1recomp](https://github.com/bryanthaboi/gen1recomp).  
Ideas drawn from PureRGB / Beyond RB / RBY Nova / Shin / community challenge culture, plus gaps vs mods you already have.

> **Before building anything new:** read [`FEATURES-DONE.md`](./FEATURES-DONE.md) — master list of features already shipped on this install. Do not recreate those.
>
> Hub for sharing: [Discord](https://bois.icu) · [mod index](https://github.com/bryanthaboi/gen1recomp-mod-index)  
> Already built by us: Battle EXP Bar, Professor Oak Challenge (Mewlax order + area HUD)

---

## Already covered (don’t rebuild)

Full detail + overlap matrix: **`FEATURES-DONE.md`**. Summary:

| Idea | Status |
| --- | --- |
| Voxel 3D overworld | `DRAMATIC_SHAPE` |
| Visible wilds in grass | `overworld_wild_spawns` |
| Battle EXP bar | `battle_exp_bar` / QoL |
| Professor Oak Challenge + area HUD | `professor_oak_challenge` |
| Nuzlocke | `nuzlocke` |
| Randomizer | `pokemon_randomizer` |
| Crystal / GS sprites, shinies | crystal + `SHINY_POKEMON` |
| Running shoes, bag, rematch, Dex tools | various installed QoL mods |
| Followers / PC anywhere / gen3 boxes | installed (often disabled) |

---

## S — High impact, great fit for Gen1Recomp

### 1. MoveDex / battle move preview
**Why:** PureRGB’s most-loved QoL — see power, accuracy, and effect text for moves you’ve seen.  
**How:** Hook move-select UI; store seen moves in `mod.save`. Partly overlaps `MOVE_MATCHUP` / `battle_move_info` — extend those with effect blurbs + PP remaining preview.

### 2. HM without a moveslot (field tools)
**Why:** #1 Gen 1 soft-lock / party-slot complaint for decades.  
**How:** Start-menu or overworld “Tools” row that runs Cut/Surf/Strength/Flash/Fly if any party mon *can* learn it (or if badge unlocked). Softlock-safe like PureRGB. Harder than running shoes; huge payoff.

### 3. Town Map wild encounter data
**Why:** PureRGB unlockable wild data — “what’s on this route?” without a wiki.  
**How:** Read `game.data.encounters[mapId]`; overlay on Town Map or a Start-menu “AREA DEX”. Pairs perfectly with Oak Challenge area HUD.

### 4. Repel reuse prompt + infinite/reusable Repel option
**Why:** Beyond RB / modern games. Tiny mod, constant quality-of-life.  
**How:** Hook item use / step counter when Repel expires → TextBox “Use another?”

### 5. Move Deleter + Move Reminder NPCs
**Why:** Gen 1 has no Move Reminder; HMs and bad TMs brick learnsets.  
**How:** Map talk scripts in Fuchsia / Indigo (Beyond RB style). Register custom script commands.

### 6. Daycare Egg / breeding lite
**Why:** Living Dex in one cartridge is a Gen 1 fantasy; Beyond RB daycare eggs.  
**How:** Daycare map script + timer/`mod.save` egg chance. Stay Gen 1–flavored (no natures/IVs UI).

---

## A — Challenge & run modes (stream-friendly)

### 7. IronMon / “no wild grind” ruleset
**Why:** Huge Twitch culture ([IronMon](https://gist.github.com/valiant-code/adb18d248fa0fae7da6b639e2ee8f9c1)).  
**How:** Gate wild battles for EXP; 1 catch/area; optional shiny clause. Compose with existing `pokemon_randomizer` + `nuzlocke` pieces rather than one mega-mod.

### 8. Level cap (gym-scaled)
**Why:** RBY Nova / modern challenge options — stops overleveling Brock at Lv40.  
**How:** Hook `battle.exp_award` / level-up; cap by badge count. Toggle per gym.

### 9. Wonder Trade / GTS lite (local or Gen1Online)
**Why:** Social Gen 1 is rare; `gen1online` exists.  
**How:** NPC that swaps a boxed mon for a seeded “wonder” from a pool or peer. Affects link fingerprint — declare `affects_link`.

### 10. “Stadium Cup” / post-game gym rematch ladder
**Why:** Beyond RB rematches; trainer_rematch already exists — theme it as a Cup with level scaling + prizes.

### 11. Soul Link / Couples Challenge UI
**Why:** Co-op challenge popular on YouTube.  
**How:** Two saves / link session: synced nicknames, shared death. Needs careful `affects_link` design.

---

## A — Presentation & atmosphere

### 12. Gen 2 day/night + weekday events
**Why:** Cookbook already sketches ToD palettes; Yellow/Crystal fans expect it.  
**How:** `world.tod` + palette hooks; optional Bug-Catching Contest schedule flavor (even if fake).

### 13. SGB / GBC border packs + themeable HUD chrome
**Why:** Cookbook R48; nostalgia flex.  
**How:** `render.letterbox` + asset packs. Low risk, high shareability.

### 14. Animated overworld tiles (water, flowers, lava)
**Why:** Crystal feel without full Crystal sprites. Complements Wilds of Kanto.

### 15. Battle transition packs / trainer intro cards
**Why:** FRLG / Stadium flair. Widescreen battle intro exists — expand to custom wipes + VS plaques.

### 16. Ambient town NPCs / seasonal Pallet
**Why:** Living world fantasy that Wilds of Kanto started. Ambient dialogue rotations, not new story.

---

## B — Dex, info, and “I wish I had a phone”

### 17. Phone / Match Call lite
**Why:** Gen 2 QoL — rematch pings, mom cash, Oak tips.  
**How:** Start-menu Phone; schedule callbacks via `mod.save` + map enter.

### 18. IV / DV viewer (optional spoiler)
**Why:** Competitive / shiny hunters. Toggle “purist hide” vs “show DVs on summary”.

### 19. Catch rate / ball calculator overlay
**Why:** Gen 1 catch math is opaque. Mash-catch exists; add a calm UI tip (“~37% with Ultra”).

### 20. Living Dex tracker (boxes + owned)
**Why:** Oak Challenge’s cousin for completionists. Grid of 151 with OWN/BOX/MISSING; export checklist.

### 21. Version-exclusive swap NPCs
**Why:** Single-cart Living Dex without trading versions (Beyond RB tradebacks).  
**How:** Post-game NPC: trade Red exclusives ↔ Blue exclusives once.

---

## B — Balance & “make the bad mons usable” (keep Gen 1 soul)

### 22. Optional learnset / TM tutor pack
**Why:** PureRGB ethos — buff weak mons without Steel/Fairy.  
**How:** `mod.content` patches behind a big options menu; default off for parity.

### 23. Physical/Special split *toggle* (controversial)
**Why:** Modern players ask constantly. Keep **off** by default; `modern_clean`-style ruleset sibling.

### 24. Set battle style + smarter AI toggle
**Why:** RBY Nova AI / Set mode for challenge. Engine already has battle style — deepen enemy switch logic carefully.

---

## C — Story / content (bigger lifts)

### 25. Bill’s Garden / Mew truck / hoax tour
**Why:** Beyond RB easter eggs; `mew_under_truck` exists — expand into a “Kanto Urban Legends” walking tour.

### 26. Mini post-game island (Pinkan / Sevii-lite)
**Why:** Fresh content without full TC. New map + 5 trainers + 1 legendary tease. Tutorial 12 path.

### 27. “Lost Beta Kanto” species/quests
**Why:** Gigaleak nostalgia (Houndour/Murkrow in Kanto, beta types). Original assets + transforms only — no ROM rips.

### 28. Rival personality branching
**Why:** Yellow/FRLG made Blue more memorable. Extra Oak-speech flags → rival text/party variants (`mod.save`).

---

## Accessibility & quality-of-life leftovers

| Idea | Notes |
| --- | --- |
| Colorblind type icons | Battle + MoveDex |
| Dyslexia-friendly font option | Letterbox / UI scale |
| One-button mash skip for text | Already partly speed/text options |
| Hold-to-run always (not B) | Toggle vs hold-B shoes |
| Auto-sort bag / key-item pocket | Bag hooks |
| Save slots UI polish | `MULTI_SAVE_SLOTS` exists — skin it |
| Speedrun practice: split timer HUD | `render.hud` / PR #347 hooks |
| Auto-relearn last move after Delete | With Move Reminder |

---

## Best next builds (opinionated shortlist)

Given what you already ship (Wilds, EXP bar, Oak Challenge, Crystal/Shiny):

1. **Town Map / Area Dex** — natural sequel to Oak Challenge area HUD  
2. **HM Tools menu** — biggest remaining Gen 1 pain  
3. **Repel reuse + Move Deleter** — small, instantly felt  
4. **IronMon ruleset** — content for streamers, composes with randomizer  
5. **Living Dex tracker** — completionist companion to Oak Challenge  

---

## Sources

- [PureRGB](https://github.com/Vortyne/pureRGB) / [FEATURES](https://github.com/Vortyne/pureRGB/blob/master/FEATURES.md) — purist QoL + MoveDex + map wild data  
- [Beyond Red and Blue](https://www.romhacking.net/hacks/9002/) — daycare eggs, rematches, overworld HMs, beta Kanto  
- [RBY Nova](https://pokemongamehack.wordpress.com/2026/05/10/pokemon-rby-nova-gb/) — AI, level caps, challenge options  
- [IronMon rules](https://gist.github.com/valiant-code/adb18d248fa0fae7da6b639e2ee8f9c1) — randomizer challenge culture  
- [Mewlax RB Oak Guide](https://docs.google.com/document/d/1gmp-piwpfUUyxnWULjQtB2m2lzWeYc-wwsXnnbyp_RY/edit) — POC progression  
- Local notes: `BEST-MODS.md`, `DISCOVERED-MODS.md`, `LEARNINGS.md`

---

*Living doc — pick an idea and we can scaffold a mod the same way as EXP bar / Oak Challenge.*
