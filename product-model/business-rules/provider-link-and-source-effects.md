---
{
  "appliesTo": [
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
      "effect": "creates"
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

# Provider links change local Account source and synchronization state

Owned-record checks; new/existing local links; old/new Account source and sync-date effects; no assumed cross-provider exclusivity.
