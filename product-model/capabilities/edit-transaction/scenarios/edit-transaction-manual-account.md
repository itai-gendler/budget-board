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
      "text": "The User submits changes to date, merchant, amount, classification or notes for the selected entries.",
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
      "text": "The Product changes Transaction facts. For Manual Account source, the previous amount/date contribution is reversed and the replacement applied to existing Balance snapshots on/after the affected date. A missing dated Balance is created from its preceding amount or zero. Eligible Recurring transaction matching can change the assignment.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Date",
            "Merchant",
            "Amount",
            "Category",
            "Subcategory",
            "Notes",
            "Recurring assignment"
          ]
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
          "as": "new-dated-balance"
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

# Edit transaction manual account

## Trigger

The User submits changes to date, merchant, amount, classification or notes for the selected entries.

## Outcome

The Product changes Transaction facts. For Manual Account source, the previous amount/date contribution is reversed and the replacement applied to existing Balance snapshots on/after the affected date. A missing dated Balance is created from its preceding amount or zero.

## Edge cases

- A missing record produces a reported error without an edit.
- An amount edit breaking the existing linked pair’s exact opposite amounts is refused.
- Recurring matching runs after edits and leaves ambiguous candidates unassigned.

## Decision points

### Is there a snapshot for the replacement date?

Is there a snapshot for the replacement date?

- Missing → reverse the prior contribution, create the dated snapshot and apply the replacement.
- Existing → reverse and reapply through existing snapshots.
