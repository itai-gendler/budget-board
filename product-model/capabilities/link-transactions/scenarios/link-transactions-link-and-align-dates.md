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
      "text": "The User chooses an opposite entry and submits the transfer pairing.",
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
      "text": "The Product links two active unlinked Transaction records on distinct Accounts with exact nonzero opposite amounts. Both receive Transfer classification and the earlier date; Manual Account source adjusts affected Balance snapshots for date movement. Candidate search’s date window is not a link-operation bound. A missing dated Balance is created for the Manual-source adjustment.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Transfer counterpart",
            "Category",
            "Subcategory",
            "Date"
          ],
          "as": "first"
        },
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Transfer counterpart",
            "Category",
            "Subcategory",
            "Date"
          ],
          "as": "second"
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Source",
            "Deletion date"
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

# Link transactions link and align dates

## Trigger

The User chooses an opposite entry and submits the transfer pairing.

## Outcome

The Product links two active unlinked Transaction records on distinct Accounts with exact nonzero opposite amounts. Both receive Transfer classification and the earlier date; Manual Account source adjusts affected Balance snapshots for date movement. Candidate search’s date window is not a link-operation bound.

## Edge cases

- An existing dated snapshot is adjusted without creating another same-date snapshot.
