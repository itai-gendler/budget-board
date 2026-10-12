---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "user",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "changes"
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
      "id": "goal",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "balance",
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

# Sync orders financial effects and can record time alongside provider errors

Source reconciliation, provider refresh/history, Goal completion, saved Rules, Last sync. Reported errors can coexist with Last sync. Default schedule eight hours, minimum interval one hour.
