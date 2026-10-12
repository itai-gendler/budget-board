---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Sync from the authenticated workspace.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated"
        }
      }
    },
    {
      "text": "Without configured providers, the Product reconciles Account.Source, completes eligible Goal records, applies saved Automatic rule, Rule condition and Rule action effects to Transaction, Balance and Tag records, and records User.Last sync. Manual-source date-changing actions can create a missing dated Balance.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "changes",
          "facts": [
            "Last sync"
          ]
        },
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Source"
          ]
        },
        {
          "entity": "goal",
          "effect": "changes",
          "facts": [
            "Completed date"
          ],
          "from": "Active",
          "to": "Completed"
        },
        {
          "entity": "automatic-rule",
          "effect": "reads",
          "facts": [
            "Conditions",
            "Actions"
          ]
        },
        {
          "entity": "rule-condition",
          "effect": "reads",
          "facts": [
            "Field",
            "Operator",
            "Comparison value"
          ]
        },
        {
          "entity": "rule-action",
          "effect": "reads",
          "facts": [
            "Field",
            "Operator",
            "Action value"
          ]
        },
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
            "Tags",
            "Transfer counterpart",
            "Deletion date",
            "Recurring assignment"
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
          "entity": "tag",
          "effect": "creates",
          "facts": [
            "Display value",
            "Normalized value"
          ],
          "as": "added"
        },
        {
          "entity": "tag",
          "effect": "removes",
          "as": "orphan"
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
          "place": "web::authenticated"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    }
  ]
}
---

# Sync no provider

## Trigger

The User chooses Sync from the authenticated workspace.

## Outcome

Without configured providers, the Product reconciles Account.Source, completes eligible Goal records, applies saved Automatic rule, Rule condition and Rule action effects to Transaction, Balance and Tag records, and records User.Last sync.
