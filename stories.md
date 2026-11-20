# Stories — <project>

Sections: Stories, Non-goals.

- Priority (Must / Should / Could) drives plan order. When a run is blocked or over budget,
  Could is dropped first, then Should. Must is never dropped without a CR.
- Acceptance criteria use EARS inside an `ears` code block, one keyword per line:

  | Keyword | Meaning | Lines per AC |
  |---|---|---|
  | `WHILE` | State that must hold | 0–1 |
  | `WHERE` | Optional feature that must be enabled | 0–1 |
  | `WHEN` | Triggering event | 0–1 |
  | `IF` | Unwanted condition (error, abuse, failure) | 0–1, not with `WHEN` |
  | `SHALL` | System response; continuation lines are indented | exactly 1 |

  - An AC with only `SHALL` is always true (ubiquitous).
  - Several actions separated by `;` are allowed only if they happen together, atomically.
- AC ids are global and stable, never renumbered. A removed AC keeps its id: `AC-n  REMOVED  vN <reason>`.

<!-- GUIDE
- Layout: id in columns 1–7, keyword in columns 8–14, text from column 15. Blank line between ACs.
- Each AC must be testable by an e2e or integration test.
- SHALL describes observable behaviour, not implementation.
- One trigger per AC. If a response holds only under an extra condition, write a separate AC.
- Roles must exist in roles.yaml, screens in design/coverage.md, entities in domain.md.
- Unknowns go to adr/ as open ADRs, never inline in this file.
-->

Roles: <role>, <role> (see `roles.yaml`).

## 1. Stories

### S-1 <Title> · <Must | Should | Could>
As a <role>, I <do something> so that <outcome>.

> Depends on <ADR-nnn> (open, <poc | spike | ask>).   <!-- delete if none -->

```ears
AC-1   WHEN   <trigger>
       SHALL  <response>

AC-2   IF     <unwanted condition>
       SHALL  <response>

AC-3   WHILE  <state>
       SHALL  <response>

AC-4   SHALL  <always-true rule>
```

## 2. Non-goals

The validator treats code for any of these as scope creep.

- <thing explicitly not built in this version>
