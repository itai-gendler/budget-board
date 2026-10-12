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
      "target": "client/src/helpers/budgets.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    }
  ]
}
---

# Budget remaining is allocation plus rollover minus signed spending

Limit plus rollover minus signed spending; projections include forecasts; parent summaries avoid duplication. Contributions and balances are not reservations/deductions. Available limit is Limit plus entering rollover. Remaining subtracts signed spending, and projected remaining also subtracts signed forecast spending. Neither Account Balance nor Asset Value nor Goal Stored contribution is deducted. Parent summaries avoid adding child allocation twice.
