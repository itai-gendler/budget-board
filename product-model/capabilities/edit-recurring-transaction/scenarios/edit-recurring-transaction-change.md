---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to the selected definition’s identifiers, destination selection, cadence, bounds or amount settings.",
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
      "text": "The Product saves Recurring transaction planning facts, amount settings, cadence and bounds. Changing its linked membership clears Transaction.Recurring assignment on formerly assigned records.",
      "kind": "product",
      "entities": [
        {
          "entity": "recurring-transaction",
          "effect": "changes",
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
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Recurring assignment"
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

# Edit recurring transaction change

## Trigger

The User submits changes to the selected definition’s identifiers, account selection, cadence, bounds or amount settings.

## Outcome

The Product saves Recurring transaction planning facts, amount settings, cadence and bounds. Changing its account clears Transaction.Recurring assignment on formerly assigned records.
