# Learning map: Kittens Game → Gardens shell

**Purpose:** Non-commercial study only. Use the public [nuclear-unicorn/kittensgame](https://github.com/nuclear-unicorn/kittensgame) repo as a *design and architecture* reference. Do **not** copy names, balance numbers, art, strings, or code wholesale. Re-implement ideas in original Gardens terms.

## Gap summary

**Already in Gardens:** 3-column shell, tick/effects, val/on buildings, system packs (Garden/Farming/Mining/Astro), basic science/jobs/craft/trade, prestige, achievements, save.

**To complete learning-scope:** offline catch-up, tooltips/options, full tech prerequisites, data-driven workshop + upgrades, village happiness, trade partners, deeper late-game missions, prestige shop, seasons/events, challenges, code modularization.

Full checklist, study file order, and “what not to copy” are in the complete document in the local package: `docs/LEARNING-FROM-KITTENS.md`.

### Study upstream in this order

1. `js/resources.js` — resource metadata  
2. `js/buildings.js` — effects, val/on, stages  
3. `game.js` — tick / managers  
4. `js/science.js` — unlock graph  
5. `js/workshop.js` — crafts  
6. `js/village.js` — jobs  
7. `js/diplomacy.js` — trade  
8. `js/space.js` — late game  
9. `js/time.js` / `js/prestige.js` — meta  

Patterns only; original content for Gardens.
