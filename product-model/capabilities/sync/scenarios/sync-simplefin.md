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
      "text": "The Product reconciles Account.Source, reads SimpleFIN connection, refreshes SimpleFIN account and SimpleFIN organization metadata, creates new Transaction history and Balance snapshots, completes eligible Goal records before Automatic rule execution through Rule condition and Rule action processing, applies Tag effects and records User.Last sync. Enabled User settings can invoke Auto categorizer and Recurring transaction matching. SimpleFIN skips deleted linked accounts, distinguishes pending TransactedAt from Posted timestamps and uses reported balance dates. Existing provider references, including deleted rows, prevent ordinary reimport; currencies are not converted.",
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
          ],
          "as": "rule-targets"
        },
        {
          "entity": "tag",
          "effect": "creates",
          "facts": [
            "Display value",
            "Normalized value"
          ],
          "as": "added-tags"
        },
        {
          "entity": "tag",
          "effect": "removes",
          "as": "orphan-tags"
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
          "entity": "simplefin-connection",
          "effect": "reads",
          "facts": [
            "Access credential"
          ]
        },
        {
          "entity": "simplefin-account",
          "effect": "changes",
          "facts": [
            "Name",
            "Currency",
            "Reported balance",
            "Balance date",
            "Last sync"
          ],
          "as": "existing-simplefin-account"
        },
        {
          "entity": "simplefin-account",
          "effect": "creates",
          "facts": [
            "Provider reference",
            "Name",
            "Currency",
            "Reported balance",
            "Balance date",
            "Sync start",
            "Last sync",
            "Local account link"
          ],
          "as": "simplefin-new",
          "with": "new-organization"
        },
        {
          "entity": "simplefin-organization",
          "effect": "changes",
          "facts": [
            "Name",
            "Domain",
            "Provider URL",
            "Institution URL",
            "Provider reference"
          ],
          "as": "existing-simplefin-organization"
        },
        {
          "entity": "simplefin-organization",
          "effect": "creates",
          "facts": [
            "Name",
            "Domain",
            "Provider URL",
            "Institution URL",
            "Provider reference"
          ],
          "as": "new-organization"
        },
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
          "as": "imported",
          "to": "Active"
        },
        {
          "entity": "balance",
          "effect": "creates",
          "facts": [
            "Date",
            "Amount"
          ],
          "as": "new-balance"
        },
        {
          "entity": "user-settings",
          "effect": "reads",
          "facts": [
            "Force-sync lookback months",
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

# Sync SimpleFIN

## Trigger

The User chooses Sync from the authenticated workspace.

## Outcome

The Product reconciles Account.Source, reads SimpleFIN connection, refreshes SimpleFIN account and SimpleFIN organization metadata, creates new Transaction history and Balance snapshots, completes eligible Goal records before Automatic rule execution through Rule condition and Rule action processing, applies Tag effects and records User.Last sync. Enabled User settings can invoke Auto categorizer and Recurring transaction matching. SimpleFIN skips deleted linked accounts, distinguishes pending TransactedAt from Posted timestamps and uses reported balance dates. Existing provider references, including deleted rows, prevent ordinary reimport; currencies are not converted.
