---
{
  "entities": [
    {
      "entity": "recurring-transaction",
      "shows": [
        "Merchant",
        "Category",
        "Subcategory",
        "Cadence",
        "Start date",
        "End date",
        "Active",
        "Amount mode",
        "Amount"
      ],
      "collects": [
        "Merchant",
        "Category",
        "Subcategory",
        "Cadence",
        "Start date",
        "End date",
        "Active",
        "Amount mode",
        "Amount"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name"
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
      "target": "server/BudgetBoard.Service/RecurringRuleService.cs"
    }
  ]
}
---

# Recurring transactions

Recurring definitions, assignments and projections. Shows and collects Account, identifying facts, cadence, bounds, active setting and amount controls.
