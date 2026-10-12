---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the monthly allocations with the default current-month selection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budgets"
        }
      }
    },
    {
      "text": "The Product reads Budget records for the current calendar month by default. Available limit is Limit plus rollover; remaining subtracts signed eligible Transaction spending. Account snapshot amount and planning contributions are not reservations.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "reads",
          "facts": [
            "Category",
            "Month",
            "Limit",
            "Rollover start"
          ]
        },
        {
          "entity": "transaction",
          "effect": "reads",
          "facts": [
            "Date",
            "Merchant",
            "Amount",
            "Category",
            "Subcategory",
            "Notes",
            "Source",
            "Provider reference",
            "Deletion date",
            "Tags",
            "Recurring assignment",
            "Transfer counterpart"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Transactions hidden"
          ]
        },
        {
          "entity": "category",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent",
            "Classification"
          ]
        },
        {
          "entity": "recurring-transaction",
          "effect": "reads",
          "facts": [
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
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budgets"
        }
      }
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

# Browse budgets current month

## Trigger

The User opens the monthly allocations with the default current-month selection.

## Outcome

The Product reads Budget records for the current calendar month by default. Available limit is Limit plus rollover; remaining subtracts signed eligible Transaction spending. Account balance and planning contributions are not reservations.
