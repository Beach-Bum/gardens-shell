# Gardens Shell

A **Kittens Game–style incremental shell** themed around gardening, with plug-in production systems (Garden, Farming, Mining, Astrophysics) and side systems (Village, Science, Workshop, Trade, Time, Achievements, Stats).

## Play

The complete game is a single file: **`index.html`** (open in any browser — no build step).

If this GitHub tree still has a short placeholder `index.html`, use the full file from the project package that was generated with this repo (same folder layout as below), then:

```bash
git clone https://github.com/Beach-Bum/gardens-shell.git
cd gardens-shell
# copy the full index.html into place, then:
git add index.html reference/
git commit -m "Add full playable shell and UI reference"
git push
```

Or simply open the local package’s `index.html` directly.

## Repo layout (shell)

```
gardens-shell/
├── index.html                 # Playable game (shell + all systems)
├── README.md
├── docs/
│   └── ARCHITECTURE.md        # How systems plug into the shell
├── css/                      # Optional future extract
├── js/                       # Optional future extract
└── reference/
    ├── ui-component-catalog.html
    ├── full-screen-demo.html
    └── systems-demo.html
```

## Shell contract

The **shell** owns layout, tick, effects bag, save/load, and tabs.  
A **system pack** only provides data (`SYSTEMS[]`: buildings, filters, unlock).

Adding a system = append to `SYSTEMS[]` + resources in `RESOURCE_DEFS`. No special-case tick logic.

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Progression

1. Garden → knowledge  
2. Farming (25 knowledge)  
3. Mining (45 knowledge)  
4. Astrophysics (100 knowledge + metal)  
5. Time / prestige → legacy seeds  

## Design reference

`reference/ui-component-catalog.html` is the visual source of truth (tokens, buttons, tables, log).
