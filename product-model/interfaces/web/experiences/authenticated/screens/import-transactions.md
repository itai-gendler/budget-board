---
{
  "entities": [
    {
      "entity": "transaction-import",
      "shows": [
        "Status",
        "Total count",
        "Processed count",
        "Cancellation requested",
        "Error summary"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name"
      ]
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

# Import transactions

CSV mapping, duplicate review and submission lead to queued processing. The progress panel presents work status, processed and total counts, cancellation state and error summary; submitted payloads, retry identity and retained processing dates are not disclosed by that panel.
