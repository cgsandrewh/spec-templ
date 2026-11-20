# Domain — <project>

<!-- GUIDE
Sections: Glossary, Entities, Lifecycles, Invariants.
Conceptual only: no column types, no storage (that's data-model.md). Changing this file is T3.
-->

## 1. Glossary

| Term | Meaning | Not to be confused with |
|---|---|---|
| <term> | <definition> | <near-synonym or —> |

## 2. Entities

| Entity | Identity | Belongs to | Lifetime |
|---|---|---|---|
| <Entity> | <internal id; human ref format if any> | <owner entity / user / —> | <deleted when / never> |

Relations: <Entity> → <Entity> (<cardinality>), ...

<Fixed enumerations, e.g. categories, if any.>

## 3. Lifecycles

### <Entity>
```
<state> ──<action>──▶ <state> ──<action>──▶ <state>
```
- Terminal: <states>.
- Editable in: <states>.

## 4. Invariants

1. <Rule that must always hold, phrased so a test can check it.>
