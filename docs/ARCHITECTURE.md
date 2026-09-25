# Architecture

## One shell, many packs

```
┌──────────────────────────────────────────┐
│ SHELL                                    │
│  resources pool · effects bag · tick     │
│  save/load · header · log · tab router   │
└──────────────────────────────────────────┘
        ▲            ▲            ▲
   ┌────┴───┐   ┌────┴───┐   ┌────┴───┐
   │ Garden │   │Farming │ … │ Astro  │
   │ pack   │   │ pack   │   │ pack   │
   └────────┘   └────────┘   └────────┘
```

## Effects bag

Each enabled building contributes keys like `cropsPerTick`, `handsMax`.
Each tick:

1. Sum effects from buildings (`on` or `val` for Max) + jobs + tech multipliers
2. Convert to per-second rates
3. Apply to resource amounts (clamped to max)
4. Run unlock + achievement checks

## Building shape

```js
{
  id: "plot",
  name: "Garden plot",
  filter: "production",       // for tab filter bar
  prices: [{ id: "seeds", base: 5 }],
  effects: { cropsPerTick: 0.4 },
  unlock: { knowledge: 10 }, // optional
  togglable: true            // optional — on/off without selling
}
```

Price scaling: `base * 1.15 ^ owned`.

## Resource shape

```js
{ id: "crops", name: "crops", group: "garden", visible: true }
```

`group` controls left-column section headers (Garden / Farming / Mining / Astrophysics / Shared).

## Tabs

- **Production tabs** = entries in `SYSTEMS[]`
- **Side tabs** = `SIDE_TABS[]` (Village, Science, Workshop, Trade, Time, Achievements, Stats)

Unlock gates use resource amounts or derived effects (e.g. `handsMax`).

## Meta vs run

| Storage key | Contents |
|-------------|----------|
| Run save | Resources, buildings, jobs, techs, calendar, log |
| Meta save | Legacy seeds, prestiges, achievements, lifetime crops |

Prestige wipes the run, keeps meta.

## Extending

1. Add resources to `RESOURCE_DEFS`
2. Push a new object onto `SYSTEMS`
3. Optional: techs in `TECH_DEFS` with `system: "yourId"`
4. Optional: jobs in `JOB_DEFS`

No changes to the tick loop required if you only use `*PerTick` and `*Max` effect keys.
