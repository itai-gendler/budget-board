---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-connection",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "simplefin-connection",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "lunchflow-connection",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "lunchflow-connection",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "simplefin-organization",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "simplefin-organization",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "simplefin-organization",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "simplefin-account",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "simplefin-account",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "simplefin-account",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SimpleFinService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/LunchFlowService.cs"
    }
  ]
}
---

# Provider connections validate credentials and retain local financial history

Distinct credential validation/discovery; disconnection clears provider data and preserves local history.
