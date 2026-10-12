---
{
  "kind": "primary",
  "routes": {
    "transactions": "Transactions",
    "transaction-details": "Transaction details",
    "dashboard": "Dashboard",
    "budget-details": "Budget details",
    "recurring-transactions": "Recurring transactions"
  },
  "steps": [
    {
      "text": "The User selects same-record financial activity and submits a new recurring definition.",
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
        },
        "recurring-transactions": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
    },
    {
      "text": "The Product creates Recurring transaction from the same-account selected records and changes Transaction.Recurring assignment. Already assigned records or mixed-account selections are refused.",
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
        },
        "recurring-transactions": {
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

# Add recurring transaction from selected transactions

## Trigger

The User selects same-record financial activity and submits a new recurring definition.

## Outcome

The Product creates Recurring transaction from the same-account selected records and changes Transaction.Recurring assignment. Already assigned records or mixed-account selections are refused.
