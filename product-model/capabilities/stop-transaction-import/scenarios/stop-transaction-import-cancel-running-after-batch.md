---
{
  "kind": "edge",
  "routes": {
    "import-transactions": "Import transactions",
    "workspace-progress": "Workspace progress"
  },
  "steps": [
    {
      "text": "The User confirms Stop while a batch is processing.",
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
      "text": "The Product records Transaction import.Cancellation requested while processing remains Running.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Cancellation requested"
          ],
          "from": "Running",
          "to": "Running"
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
    },
    {
      "text": "After its current batch and progress update, the Product marks Transaction import Cancelled and records Completed date. Committed rows remain.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Status",
            "Completed date"
          ],
          "from": "Running",
          "to": "Cancelled"
        }
      ],
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

# Stop transaction import cancel running after batch

## Trigger

The User confirms Stop while a batch is processing.

## Outcome

The Product records Transaction import.Cancellation requested; a Running worker finishes its current batch, keeps committed rows and then marks the work Cancelled.
