---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User keeps duplicate-review matches and submits the mapped CSV rows.",
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
      "text": "The duplicate-review choice keeps submitted rows matching existing date, amount and mapped destination identifiers; the Product creates Pending Transaction import work for them rather than removing those rows.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "creates",
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
          ],
          "to": "Pending"
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

# Import transactions keep duplicates

## Trigger

The User keeps duplicate-review matches and submits the mapped CSV rows.

## Outcome

The duplicate-review choice keeps submitted rows matching existing date/amount/mapped-account records; the Product creates Pending Transaction import work for them rather than removing those rows.
