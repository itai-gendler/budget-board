---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "auto-categorizer",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "auto-categorizer",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "auto-categorizer",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "user-settings",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "user-settings",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/AutomaticTransactionCategorizerHelper.cs"
    }
  ]
}
---

# Categorization requires eligible training data and accepted enabled predictions

Eligible categorized merchant-bearing training data on nondeleted Accounts; model required for activation; accepted enabled prediction can replace supplied category, otherwise preserves it. No prediction-quality promise.
