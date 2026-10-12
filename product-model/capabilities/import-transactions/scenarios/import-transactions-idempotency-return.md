---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User resubmits work with an existing retry key, possibly with a different payload.",
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
      "text": "An existing trimmed Retry key returns the existing Transaction import without accepting a second job.",
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

# Import transactions idempotency return

## Trigger

The User resubmits work with an existing retry key, possibly with a different payload.

## Outcome

An existing trimmed Retry key returns the existing Transaction import without accepting a second job.
