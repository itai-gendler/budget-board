---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The enabled synchronization schedule is due.",
      "kind": "condition",
      "entities": [],
      "unattended": true,
      "contexts": {
        "web": {
          "place": "web::authenticated"
        }
      }
    },
    {
      "text": "At the enabled synchronization interval, the Product reconciles Account.Source, reads SimpleFIN connection and LunchFlow connection, refreshes SimpleFIN organization, SimpleFIN account and LunchFlow account, imports Transaction history and Balance snapshots, completes eligible Goal records, runs Automatic rule with Rule condition and Rule action effects including Tag cleanup, then records User.Last sync. User settings, Auto categorizer and Recurring transaction processing retain their ordinary behavior. Per-user failures are isolated by the job.",
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

# Sync unattended schedule

## Trigger

The enabled synchronization schedule is due.

## Outcome

At the enabled synchronization interval, the Product reconciles Account.Source, reads SimpleFIN connection and LunchFlow connection, refreshes SimpleFIN organization, SimpleFIN account and LunchFlow account, imports Transaction history and Balance snapshots, completes eligible Goal records, runs Automatic rule with Rule condition and Rule action effects including Tag cleanup, then records User.Last sync. User settings, Auto categorizer and Recurring transaction processing retain their ordinary behavior. Per-user failures are isolated by the job.
