# Design

**Fidelity: pixel-perfect.** The export is the source of truth for layout, spacing, typography,
colour and component states. The agent does not invent UI.

## 1. Contents

```
design/
  export/       # design export (HTML + assets + tokens), unchanged as delivered
  coverage.md   # screen × state matrix
```

## 2. How it's consumed

1. **Coverage gate**: every screen referenced by an AC exists and every required state is
   `covered`. Any `gap` blocks the run; the designer closes it.
2. **Decomposition**: the agent extracts tokens, primitives and components into the design
   system, plus a catalogue page per component × state.
3. **Approval**: a human checks the catalogue against the export (part of H1). Tokens and
   baselines are protected from then on.
4. **During the loop**: screens use only design-system components; visual regression runs at L3.

A screen or state discovered missing during the run is a T2 CR (design gap), not an assumption.
