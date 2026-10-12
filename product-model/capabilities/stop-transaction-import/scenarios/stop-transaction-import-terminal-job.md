---
{
  "kind": "edge",
  "routes": {
    "import-transactions": "Import transactions",
    "workspace-progress": "Workspace progress"
  },
  "steps": [
    {
      "text": "The User requests Stop for a job that has already reached a terminal result.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "import-transactions": {
          "place": "web::authenticated::import-transactions"
        },
        "workspace-progress": {
          "place": "web::authenticated"
        }
      }
    },
    {
      "text": "Stopping terminal Transaction import work returns its existing terminal state without undoing completed rows.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "reads",
          "facts": [
            "Submitted work",
            "Status",
            "Total count",
            "Processed count",
            "Succeeded count",
            "Failed count",
            "Retry key",
            "Cancellation requested",
            "Error summary",
            "Created date",
            "Started date",
            "Completed date"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "import-transactions": {
          "place": "web::authenticated::import-transactions"
        },
        "workspace-progress": {
          "place": "web::authenticated"
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

# Stop transaction import terminal job

## Trigger

The User requests Stop for a job that has already reached a terminal result.

## Outcome

Stopping terminal Transaction import work returns its existing terminal state without undoing completed rows.
