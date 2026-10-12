---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits CSV rows after column mapping, destination mapping and duplicate review.",
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
      "text": "The Product creates Pending Transaction import work with the mapped rows, retry identity and initial progress facts.",
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
    },
    {
      "text": "The Product claims Transaction import as Running and initializes its first Started date.",
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
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "The Product creates valid Transaction rows through ordinary classification and recurring matching. Account.Source controls changes to existing Balance amounts and creation of missing dated snapshots. Transaction import progress is saved after each batch.",
      "kind": "product",
      "actor": "user",
      "entities": [
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
          "as": "existing-balances"
        },
        {
          "entity": "balance",
          "effect": "creates",
          "facts": [
            "Date",
            "Amount"
          ],
          "as": "new-dated-balance"
        },
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Processed count",
            "Succeeded count",
            "Failed count",
            "Error summary"
          ]
        }
      ],
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "Transaction import reaches Completed with recorded successful counts.",
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

# Import transactions complete

## Trigger

The User submits CSV rows after column mapping, account mapping and duplicate review.

## Outcome

The Product accepts mapped rows as a Pending Transaction import and completes asynchronous processing. Valid rows become Transaction records; classification, recurring assignment and Manual Account-source Balance effects use ordinary creation behavior.

## Edge cases

- A demo-filter submission refusal starts no import work.
- A trimmed Retry key longer than two hundred characters is refused.
