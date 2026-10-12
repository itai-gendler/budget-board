---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "asset",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "value",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "goal",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#ReadGoalsAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Models/Account.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Models/Asset.cs"
    }
  ]
}
---

# Current amounts use the latest dated snapshot

Current amount selects the latest dated snapshot; Goal calculations do not impose an as-of-today cutoff.
