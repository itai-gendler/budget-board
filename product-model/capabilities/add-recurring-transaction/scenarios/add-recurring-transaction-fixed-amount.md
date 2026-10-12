---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits cadence and bounds with a configured signed amount.",
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
      "text": "The Product creates Recurring transaction with supplied account association, identifying facts, active setting, validated cadence and inclusive bounds, using the configured Amount.",
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

# Add recurring transaction fixed amount

## Trigger

The User submits cadence and bounds with a configured signed amount.

## Outcome

The Product creates Recurring transaction with supplied account association, identifying facts, active setting, validated cadence and inclusive bounds, using the configured Amount.
