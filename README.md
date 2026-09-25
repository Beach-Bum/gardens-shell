# Gardens Shell

A **Kittens Game–style incremental shell** themed around gardening, with plug-in production systems (Garden, Farming, Mining, Astrophysics) and side systems (Village, Science, Workshop, Trade, Time, Achievements, Stats).

Open `index.html` in a browser — no build step, no server required.

## Quick start

```bash
# from this folder
open index.html
# or
python3 -m http.server 8080
```

## Repo layout

```
gardens-shell/
├── index.html                 # Playable game (shell + all systems)
├── README.md
├── docs/
│   └── ARCHITECTURE.md        # How systems plug into the shell
└── reference/
    ├── ui-component-catalog.html   # Design tokens + UI components
    ├── full-screen-demo.html       # Dense layout reference
    └── systems-demo.html           # Minimal multi-system demo
```

## Shell contract

The **shell** owns:

| Concern | Responsibility |
|--------|----------------|
| Layout | Resources left · actions center · log right · header |
| Tick | Fixed timestep, effects bag, unlock checks |
| Save | `localStorage` run save + meta (legacy / achievements) |
| Tabs | Production systems + side tabs |
| UI patterns | Buttons (on/val, sell, toggle), filters, resource table |

A **system pack** only provides data:

- `id`, `label`, `blurb`
- `unlock` — when the tab appears
- `filters` — All · Available · domain filters
- `buildings[]` — prices, effects, optional `togglable` / unlock

Adding a system = append to `SYSTEMS[]` and add resources to `RESOURCE_DEFS`. No special-case tick logic.

## Progression (default content)

1. **Garden** — plant / water / knowledge  
2. **Farming** — grain, livestock (25 knowledge)  
3. **Mining** — stone, ore, metal (45 knowledge)  
4. **Astrophysics** — data, fuel, insight (100 knowledge + metal)  
5. **Time** — chronoboost, prestige → legacy seeds  

## Design reference

Use `reference/ui-component-catalog.html` as the single visual source of truth (tokens, buttons, tables, cards, log, dialogs). Keep new screens composed from those patterns.

## License / notes

Original shell and content for the Gardens project. Patterns inspired by common incremental-game architecture; not a copy of any specific commercial title's assets or balance.
