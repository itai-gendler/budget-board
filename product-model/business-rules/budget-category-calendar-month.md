---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "budget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "budget",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#CreateBudgetsAsync"
    }
  ]
}
---

# Budgets are unique by category and calendar month

Category/year/month uniqueness; partial creation batches; no universal normalized-day guarantee.
