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
      "text": "The User chooses Unlink for the selected transfer pair.",
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
      "text": "The Product clears Transfer counterpart on both Transaction records while retaining earlier Date and Transfer classification/Subcategory changes.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Transfer counterpart"
          ],
          "as": "first"
        },
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Transfer counterpart"
          ],
          "as": "second"
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
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    }
  ]
}
---

# Unlink transactions unlink without reversing classification

## Trigger

The User chooses Unlink for the selected transfer pair.

## Outcome

The Product clears Transfer counterpart on both Transaction records while retaining earlier Date and Transfer Category/Subcategory changes.
