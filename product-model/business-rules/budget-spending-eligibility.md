---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
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
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    }
  ]
}
---

# Budget spending follows its specific transaction eligibility

Deleted Transactions, hidden Transactions and Hide from Budgets excluded; no independent Account-deleted/Account-hidden exclusion.
