# forgekit spec bundle — template

Copy this folder, fill it in, run `fgk init --spec <folder>`.
A filled-in example lives in `forgekit-sample/` (Tally).

## Conventions

- `<angle brackets>` are placeholders. Spec-lint fails if any remain.
- `<!-- ... -->` and `# ...` lines starting with `TODO`/`GUIDE` are guidance; delete them when done.
- Every file has fixed sections, listed at its top. Keep them all; write `—` or `~` when one doesn't apply.
- One fact lives in one file. Elsewhere, refer to it by id: `S-1`, `AC-1`, `ADR-001`, `C-1`, `DG-1`.
- Decisions live only in `adr/`. Other files state what is, not why.
- Every quantitative requirement names the check that enforces it.

## Files

| File | Holds | Becomes |
|---|---|---|
| `project.yaml` | Meta, NFR profile + numbers, constraints | Infra sizing, verify thresholds, risk.yaml defaults |
| `stories.md` | Stories, AC-n, priority, non-goals | Protected acceptance + e2e tests, plan order |
| `domain.md` | Glossary, entities, lifecycles, invariants | Domain logic and its tests |
| `data-model.md` | Stores, tables, indexes, objects, retention, sensitive-data rules | Migrations, retention jobs, risk tags |
| `roles.yaml` | Permissions matrix | Generated authorization policy + tests |
| `architecture.md` | Components, external systems, communication, environments | Infra stacks, deployables |
| `contracts/` | HTTP API (OpenAPI), async messages, external file/payload samples | Contract tests, generated types |
| `integrations.yaml` | Third-party services, fakes, sandboxes, failure modes | Adapters + fakes, contract tests |
| `codebase.md` | Project structure, code rules + enforcing tool | Lint / dependency / semgrep config |
| `design/` | Design export (pixel-perfect), screen × state coverage | Design system + components before the loop |
| `adr/` | Every decision, made or open | Binding constraints; POC/spike tasks first |
| `risk.yaml` | What the agent may decide alone | Decision tiers, PR risk triggers |

Not in the bundle: seed/demo data (agent generates it), approvers (git platform: CODEOWNERS, branch protection).

## Suggested fill order

1. `project.yaml` → `stories.md` → `domain.md` → `roles.yaml`
2. `design/` export + `coverage.md`
3. `architecture.md` → `integrations.yaml` → `contracts/` → `data-model.md`
4. `adr/` — record each decision as it comes up in steps 1–3; anything unsure becomes an `open` ADR
5. `codebase.md`, `risk.yaml` (start from template defaults)

## Pre-loop gates (before `fgk run`)

1. **Spec lint**: no placeholders, all sections present, every story has ≥ 1 testable AC,
   every referenced role / entity / endpoint / message / ADR exists.
2. **Design coverage**: no `gap` in `design/coverage.md`.
3. **Design decomposition**: agent builds the design system from the export; a human approves it.
4. **Open ADRs**: `poc` / `spike` run first; `ask` needs an answer, or its stated default, by H1.
