---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits cadence and bounds with automatic amount estimation.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
    },
    {
      "text": "The Product creates Recurring transaction with automatic Amount mode. At least two assigned nondeleted amounts supply a median estimate; otherwise the configured Amount remains the forecast amount.",
      "kind": "product",
      "entities": [
        {
          "entity": "recurring-transaction",
          "effect": "creates",
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
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
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

# Add recurring transaction automatic amount

## Trigger

The User submits cadence and bounds with automatic amount estimation.

## Outcome

The Product creates Recurring transaction with automatic Amount mode. At least two assigned nondeleted amounts supply a median estimate; otherwise the configured Amount remains the forecast amount.
