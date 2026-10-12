---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User inspects a rollover classification across earlier budgeted and unbudgeted months.",
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
      "text": "The Product accumulates Budget limit minus signed eligible Transaction spending only for earlier months retaining that category’s allocation. Unbudgeted months and their spending are skipped, deficits remain and a nonrolling parent can sum child rollover.",
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

# Browse budgets rollover and gaps

## Trigger

The User inspects a rollover category across earlier budgeted and unbudgeted months.

## Outcome

The Product accumulates Budget limit minus signed eligible Transaction spending only for earlier months retaining that category’s allocation. Unbudgeted months and their spending are skipped, deficits remain and a nonrolling parent can sum child rollover.
