---
{
  "entities": [
    {
      "entity": "budget",
      "shows": [
        "Category",
        "Month",
        "Limit",
        "Rollover start"
      ],
      "collects": [
        "Category",
        "Month",
        "Limit",
        "Rollover start"
      ]
    },
    {
      "entity": "category",
      "shows": [
        "Name",
        "Parent",
        "Classification"
      ]
    },
    {
      "entity": "transaction",
      "shows": [
        "Date",
        "Merchant",
        "Amount",
        "Category",
        "Subcategory",
        "Notes",
        "Tags",
        "Recurring assignment",
        "Transfer counterpart"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/budgets.ts"
    }
  ]
}
---

# Budgets

Selected monthly Budget collection. Shows and collects Category, Month, Limit and Rollover start. Actual, available and projected amounts are derived outputs.
