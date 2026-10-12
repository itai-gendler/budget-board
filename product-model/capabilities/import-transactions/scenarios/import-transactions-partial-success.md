---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User observes processing of accepted rows whose batch contains both successful and failed rows.",
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
      "text": "The Product completes Transaction import with both successes and errors. Committed Transaction rows and Manual-source Balance effects remain; failed rows are reported. Hundred-row batch failure falls back to individual row attempts.",
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
            "Error summary",
            "Completed date"
          ],
          "from": "Running",
          "to": "Completed with errors"
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

# Import transactions partial success

## Trigger

The User observes processing of accepted rows whose batch contains both successful and failed rows.

## Outcome

The Product completes Transaction import with both successes and errors. Committed Transaction rows and Manual-source Balance effects remain; failed rows are reported. Hundred-row batch failure falls back to individual row attempts.
