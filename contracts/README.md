# Contracts

Interfaces the code must match exactly. Changing any file here is T2.

| File | Use for |
|---|---|
| `http-api.yaml` | HTTP API (OpenAPI 3.1) |
| `messages.yaml` | Queue / event messages |
| `<name>.<csv\|json\|xml>` | A real sample of any external format you don't own (file import/export, webhook payload). Referenced from `integrations.yaml › contract` and the ACs that produce it |

If an external format isn't known yet, open an `ask` ADR. Never let the agent guess it.
