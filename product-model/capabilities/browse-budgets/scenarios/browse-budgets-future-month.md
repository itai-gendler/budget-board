---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects a future calendar month for monthly spending analysis.",
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
      "text": "The Product presents the selected future Budget month and eligible Recurring transaction forecasts. Summary actual spending stops at today while category queried rows can include future-dated Transaction records.",
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

# Browse budgets future month

## Trigger

The User selects a future calendar month for Budget analysis.

## Outcome

The Product presents the selected future Budget month and eligible Recurring transaction forecasts. Summary actual spending stops at today while category queried rows can include future-dated Transaction records.
