---
{
  "kind": "primary",
  "routes": {
    "transactions": "Transactions",
    "transaction-details": "Transaction details",
    "dashboard": "Dashboard",
    "budget-details": "Budget details"
  },
  "steps": [
    {
      "text": "The User clears the recurring assignment on selected financial activity entries.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "transactions": {
          "place": "web::authenticated::transactions"
        },
        "transaction-details": {
          "place": "web::authenticated::transaction-details"
        },
        "dashboard": {
          "place": "web::authenticated::dashboard"
        },
        "budget-details": {
          "place": "web::authenticated::budget-details"
        }
      }
    },
    {
      "text": "The Product clears selected Transaction.Recurring assignment.",
      "kind": "product",
      "entities": [
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
        "transactions": {
          "place": "web::authenticated::transactions"
        },
        "transaction-details": {
          "place": "web::authenticated::transaction-details"
        },
        "dashboard": {
          "place": "web::authenticated::dashboard"
        },
        "budget-details": {
          "place": "web::authenticated::budget-details"
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

# Unassign recurring transaction clear

## Trigger

The User clears the recurring assignment on selected financial activity entries.

## Outcome

The Product clears selected Transaction.Recurring assignment.
