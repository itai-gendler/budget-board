---
{
  "kind": "primary",
  "routes": {
    "transactions": "Transactions",
    "transaction-details": "Transaction details"
  },
  "steps": [
    {
      "text": "The User opens the financial activity collection, applies search or filters and inspects a selected entry.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "transactions": {
          "place": "web::authenticated::transactions"
        },
        "transaction-details": {
          "place": "web::authenticated::transaction-details"
        }
      }
    },
    {
      "text": "The Product presents active Transaction facts for the selected search, dates, account/classification/label filters and details. Hidden-account transaction settings apply; the general list includes the reserved excluded-planning classification.",
      "kind": "product",
      "entities": [
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
            "Name",
            "Transactions hidden"
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

# Browse transactions active search filter and detail

## Trigger

The User opens the financial activity collection, applies search or filters and inspects a selected entry.

## Outcome

The Product presents active Transaction facts for the selected search, dates, account/category/tag filters and details. Hidden-account transaction settings apply; the general list includes Hide from Budgets categories.
