---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "Pending submitted work is available for the import worker to claim.",
      "kind": "condition",
      "entities": [],
      "unattended": true,
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "The worker claims Transaction import and records its start.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Status",
            "Started date"
          ],
          "from": "Pending",
          "to": "Running"
        }
      ],
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "The worker claims Pending Transaction import as Running, processes rows and records counts and terminal status. Valid Transaction records use ordinary classification, recurring matching and Manual-source Balance behavior.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Status",
            "Processed count",
            "Succeeded count",
            "Failed count",
            "Completed date"
          ],
          "from": "Running",
          "to": "Completed"
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
          "as": "existing-balance"
        },
        {
          "entity": "balance",
          "effect": "creates",
          "facts": [
            "Date",
            "Amount"
          ],
          "as": "missing-dated-balance"
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
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionImportService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/transactionImport.ts"
    }
  ]
}
---

# Import transactions unattended processing

## Trigger

Pending submitted work is available for the import worker to claim.

## Outcome

The worker claims Pending Transaction import as Running, processes rows and records counts and terminal status. Valid Transaction records use ordinary classification, recurring matching and Manual-source Balance behavior.
