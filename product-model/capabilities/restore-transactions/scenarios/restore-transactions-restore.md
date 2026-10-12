---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Restore for selected deleted financial activity entries.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-transactions"
        }
      }
    },
    {
      "text": "The Product clears Transaction.Deletion date and reapplies its signed contribution to Balance snapshots for Manual Account source. Prior classification, label and transfer links are not reconstructed. A missing dated Balance is created for the Manual-source adjustment.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Deletion date"
          ],
          "from": "Deleted",
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
          "as": "missing-dated-balance"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-transactions"
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

# Restore transactions restore

## Trigger

The User chooses Restore for selected deleted financial activity entries.

## Outcome

The Product clears Transaction.Deletion date and reapplies its signed contribution to Balance snapshots for Manual Account source. Prior classification, Tags and transfer links are not reconstructed.

## Edge cases

- Repeated restoration can repeat monetary adjustment.



- An existing dated snapshot is adjusted without creating another same-date snapshot.
