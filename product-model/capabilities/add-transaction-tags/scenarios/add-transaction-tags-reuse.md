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
      "text": "The User submits the labels to add to selected financial activity entries.",
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
      "text": "The Product finds a Tag by its normalized spelling and adds it to selected Transaction.Tags without creating a duplicate label.",
      "kind": "product",
      "entities": [
        {
          "entity": "tag",
          "effect": "reads",
          "facts": [
            "Display value",
            "Normalized value"
          ]
        },
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Tags"
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
      "target": "server/BudgetBoard.Service/TagService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    }
  ]
}
---

# Add transaction tags reuse

## Trigger

The User submits the labels to add to selected financial activity entries.

## Outcome

The Product finds a Tag by its normalized spelling and adds it to selected Transaction.Tags without creating a duplicate label.
