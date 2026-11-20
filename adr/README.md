# Decisions — <project>

Every decision about the system, made or open. Other files refer to decisions by id and never
restate them. New ADR: copy `_template.md` to `NNN-short-title.md` and add a row to the index.

## Status

| Status | Meaning | Agent may change it? |
|---|---|---|
| `accepted` | Binding | No. Reopening needs a CR at the ADR's tier |
| `proposed` | Starting point | Yes, with a superseding ADR at T0/T1 |
| `open` | Not decided; resolved by the method below before dependent work | Agent runs `poc` / `spike`; humans answer `ask` |
| `superseded` | Replaced; kept for history | — |

## Resolution methods (open ADRs)

| Method | Who | Output |
|---|---|---|
| `poc` | Agent: throwaway code in `spikes/ADR-NNN/` against the real or sandbox service | Evidence + `accepted` ADR, or the fallback as a CR |
| `spike` | Agent: experiment inside the app skeleton | Same |
| `ask` | Human: business or legal question no experiment can answer | Answer recorded in the ADR |

POC and spike code is never merged. Budgets count against `risk.yaml › autonomy.spike_budget`.

## Tiers

| Tier | Example | Decided by |
|---|---|---|
| T0 | Implementation detail | agent |
| T1 | Gap-filling assumption | agent, logged |
| T2 | Spec amendment | human, via CR |
| T3 | One-way door (data model, identity, auth, stack, money) | human, via CR + migration plan |

## Index

| ADR | Title | Status | Tier | Resolve by | Blocks |
|---|---|---|---|---|---|
| [001](001-<title>.md) | <title> | <status> | <T0–T3> | <— / poc / spike / ask> | <S-n / AC-n / —> |
