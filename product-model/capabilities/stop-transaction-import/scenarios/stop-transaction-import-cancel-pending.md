---
{
  "kind": "primary",
  "routes": {
    "import-transactions": "Import transactions",
    "workspace-progress": "Workspace progress"
  },
  "steps": [
    {
      "text": "The User confirms Stop while the job is still queued.",
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
      "text": "Pending Transaction import cancellation immediately records Cancellation requested, Cancelled status and Completed date.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Cancellation requested",
            "Status",
            "Completed date"
          ],
          "from": "Pending",
          "to": "Cancelled"
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

# Stop transaction import cancel pending

## Trigger

The User confirms Stop while the job is still queued.

## Outcome

Pending Transaction import cancellation immediately records Cancellation requested, Cancelled status and Completed date.
