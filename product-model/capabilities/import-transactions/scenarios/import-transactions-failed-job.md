---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens progress for submitted work while processing is Running and an unrecoverable failure occurs.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "Unrecoverable processing failure marks Transaction import Failed with Error summary and Completed date; committed rows remain.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Status",
            "Error summary",
            "Completed date"
          ],
          "from": "Running",
          "to": "Failed"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "The Product presents Transaction import status, processed and total counts, cancellation state and error summary in the authenticated workspace.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "reads",
          "facts": [
            "Status",
            "Processed count",
            "Total count",
            "Cancellation requested",
            "Error summary"
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
      "target": "server/BudgetBoard.Service/TransactionImportService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/transactionImport.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/components/TransactionImportJobPanel/TransactionImportJobPanel.tsx#TransactionImportJobPanel"
    }
  ]
}
---

# Import transactions failed job

## Trigger

The User opens progress for submitted work while processing is Running and an unrecoverable failure occurs.

## Outcome

Unrecoverable processing failure marks Transaction import Failed with Error summary and Completed date; committed rows remain.
