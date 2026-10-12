---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects the destination and submits date, merchant, amount, classification and notes.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::transactions"
        }
      }
    },
    {
      "text": "The Product creates Transaction facts. Eligible enabled Auto categorizer predictions can replace supplied classification; otherwise supplied classification remains. Unique Recurring transaction matching sets the assignment when unambiguous. Provider Account source leaves local snapshot amounts unchanged by this ledger operation.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "creates",
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
          ],
          "to": "Active"
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Source"
          ]
        },
        {
          "entity": "user-settings",
          "effect": "reads",
          "facts": [
            "Auto categorizer enabled",
            "Minimum probability percentage"
          ]
        },
        {
          "entity": "auto-categorizer",
          "effect": "reads",
          "facts": [
            "Trained classifier"
          ]
        },
        {
          "entity": "recurring-transaction",
          "effect": "reads",
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
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::transactions"
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

# Add transaction provider account

## Trigger

The User selects the destination account and submits date, merchant, amount, classification and notes.

## Outcome

The Product creates Transaction facts. Eligible enabled Auto categorizer predictions can replace supplied Category; otherwise supplied classification remains. Unique Recurring transaction matching sets the assignment when unambiguous. Provider Account source leaves local snapshot amounts unchanged by this ledger operation.

## Edge cases

- Prediction is used only with enabled settings, retained model and an accepted probability; no classifier-quality guarantee follows.
