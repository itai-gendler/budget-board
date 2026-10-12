---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to date, merchant, amount, classification or notes for the selected entries.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budget-details"
        }
      }
    },
    {
      "text": "The Product saves selected Transaction Date, Merchant, Amount, classification, Subcategory and Notes from this host. Account.Source determines whether Balance adjustments reverse and reapply the monetary contribution. Eligible Recurring transaction matching can change the assignment.",
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
        "web": {
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

# Edit transaction budget inline

## Trigger

The User submits changes to date, merchant, amount, classification or notes for the selected entries.

## Outcome

The Product saves selected Transaction Date, Merchant, Amount, Category, Subcategory and Notes from this host. Account.Source determines whether Balance adjustments reverse and reapply the monetary contribution.

## Edge cases

- An amount edit that breaks an existing linked pair’s exact opposite amounts is refused.
- Recurring matching runs after edits; an ambiguous candidate remains unassigned.
