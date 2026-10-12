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
      "text": "The Product creates Transaction facts. Eligible enabled Auto categorizer predictions can replace supplied classification; otherwise supplied classification remains. Unique Recurring transaction matching sets the assignment when unambiguous. For Manual Account source, signed amount is added to existing Balance snapshots on/after the affected date. A missing dated Balance is created from its preceding amount or zero.",
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
        },
        {
          "entity": "balance",
          "effect": "changes",
          "facts": [
            "Amount"
          ],
          "as": "existing-balances"
        },
        {
          "entity": "balance",
          "effect": "creates",
          "facts": [
            "Date",
            "Amount"
          ],
          "as": "new-dated-balance"
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

# Add transaction manual account

## Trigger

The User selects the destination account and submits date, merchant, amount, classification and notes.

## Outcome

The Product creates Transaction facts. Eligible enabled Auto categorizer predictions can replace supplied Category; otherwise supplied classification remains. Unique Recurring transaction matching sets the assignment when unambiguous. For Manual Account source, signed amount is added to existing Balance snapshots on/after the affected date. A missing dated Balance is created from its preceding amount or zero.

## Edge cases

- Prediction is used only with enabled settings, retained model and an accepted probability; no classifier-quality guarantee follows.

## Decision points

### Is there a snapshot for the transaction date?

Is there a snapshot for the transaction date?

- Missing → create it from the preceding amount or zero and adjust later snapshots.
- Existing → adjust its Amount and later snapshots without another creation.
