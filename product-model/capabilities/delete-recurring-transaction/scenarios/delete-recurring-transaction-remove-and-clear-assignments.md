---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected recurring definition.",
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
      "text": "The Product removes Recurring transaction and clears corresponding Transaction.Recurring assignment.",
      "kind": "product",
      "entities": [
        {
          "entity": "recurring-transaction",
          "effect": "removes"
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

# Delete recurring transaction remove and clear assignments

## Trigger

The User confirms removal of the selected recurring definition.

## Outcome

The Product removes Recurring transaction and clears corresponding Transaction.Recurring assignment.
