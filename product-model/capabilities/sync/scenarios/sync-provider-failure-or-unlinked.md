---
{
  "kind": "edge",
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
      "text": "Provider or unlinked-record errors are reported while successful SimpleFIN account, LunchFlow account, SimpleFIN organization, Transaction and Balance effects remain. Account sources are reconciled; Goal completion precedes Automatic rule, Rule condition and Rule action processing with Tag effects. User.Last sync can still change. User settings, Auto categorizer and Recurring transaction behavior apply to accepted new records; neither total rollback nor provider reliability is guaranteed.",
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
          "entity": "lunchflow-connection",
          "effect": "reads",
          "facts": [
            "API credential"
          ]
        },
        {
          "entity": "lunchflow-account",
          "effect": "changes",
          "facts": [
            "Name",
            "Institution name",
            "Provider",
            "Status",
            "Currency",
            "Reported balance",
            "Balance date",
            "Last sync"
          ],
          "as": "existing-lunchflow-account"
        },
        {
          "entity": "lunchflow-account",
          "effect": "creates",
          "facts": [
            "Provider reference",
            "Name",
            "Institution name",
            "Provider",
            "Status",
            "Currency",
            "Reported balance",
            "Balance date",
            "Sync start",
            "Last sync",
            "Local account link"
          ],
          "as": "lunchflow-new"
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

# Sync provider failure or unlinked

## Trigger

The User chooses Sync from the authenticated workspace.

## Outcome

Provider or unlinked-record errors are reported while successful SimpleFIN account, LunchFlow account, SimpleFIN organization, Transaction and Balance effects remain. Account sources are reconciled; Goal completion precedes Automatic rule, Rule condition and Rule action processing with Tag effects. User.Last sync can still change. User settings, Auto categorizer and Recurring transaction behavior apply to accepted new records; neither total rollback nor provider reliability is guaranteed.
