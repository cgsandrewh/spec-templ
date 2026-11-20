# Architecture — <project>

<!-- GUIDE
Sections: System context, Components, Communication, Key flows, Environments.
System level only: what runs, what it talks to, how. No code structure (codebase.md),
no storage detail (data-model.md), no rationale (adr/).
-->

## 1. System context

```
<ASCII diagram: users → components → external systems>
```

| External system | Used for | Contract |
|---|---|---|
| <system> | <purpose> | <integrations.yaml#name / contracts/...> |

## 2. Components

| Component | Responsibility | Runtime | Owns |
|---|---|---|---|
| <component> | <what it does> | <where it runs> | <data / schema / —> |

<ADR references for the shape of the system.>

## 3. Communication

| From | To | Mechanism | Sync? | Contract |
|---|---|---|---|---|
| <component> | <component> | <HTTPS / queue / event / SQL> | <sync / async> | <contracts/... > |

## 4. Key flows

**<Flow name>**
1. <step>
2. <step>

## 5. Environments

| Environment | Where | Integrations |
|---|---|---|
| local | `fgk` work container | Fakes |
| preview | Per-run AWS sandbox stack | Vendor sandboxes |
| production | Out of forgekit scope | — |
