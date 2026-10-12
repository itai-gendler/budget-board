---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "budget",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "recurring-transaction",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    }
  ]
}
---

# Actual and projected Budget amounts use distinct date scopes

Summary actual through today, forecast from today; category actual may include future rows; forecast failure preserves actuals.
