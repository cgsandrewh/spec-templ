# Data model — <project>

<!-- GUIDE
Sections: Stores, Tables, Indexes, Object storage, Retention, Sensitive data.
Physical form of domain.md. Column tags (pii, financial, ...) feed risk.yaml.
Changing a table or retention rule is T2; identity columns are T3.
Write "None" for a section that doesn't apply (e.g. no cache, no object storage).
-->

## 1. Stores

| Store | Technology | Holds | Backup / recovery |
|---|---|---|---|
| <main DB> | <Postgres, RDS> | <what> | <PITR n days — matches project.yaml rpo> |
| <bucket> | <S3> | <what> | <...> |
| <cache> | <— / Redis> | <None in v1> | — |

## 2. Tables

Conventions: <id type, timestamps, money representation (ADR-nnn)>.

### <table>
| Column | Type | Null | Constraints | Tags |
|---|---|---|---|---|
| <column> | <type> | <yes/no> | <unique / fk / check> | <pii / financial / —> |

<Notes: append-only, grants, triggers.>

## 3. Indexes

| Table | Index | Serves |
|---|---|---|
| <table> | <(columns) where ...> | <screen / query / job> |

## 4. Object storage

| Prefix | Content | Written by | Read via | Lifecycle |
|---|---|---|---|---|
| `<prefix>/{id}` | <what> | <component> | <pre-signed GET, ttl> | <expiry / deleted with ...> |

## 5. Retention

| Data | Kept | Then | Done by |
|---|---|---|---|
| <data> | <duration after event> | <hard delete / pseudonymise> | <job / lifecycle rule> |

## 6. Sensitive data

| Tag | Rule |
|---|---|
| pii | <e.g. never logged; included in user export; replaced on pseudonymisation> |
