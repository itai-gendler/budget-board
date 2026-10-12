---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an invalid column/financial-record mapping, malformed work or excessive retry key.",
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
      "text": "The browser requires valid mapping before submission. Malformed submitted work or an invalid retry identity reports refusal without accepting new work; row validation failures after enqueue are reported through job progress.",
      "kind": "condition",
      "entities": [],
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

# Import transactions invalid mapping or work

## Trigger

The User submits an invalid column/financial-record mapping, malformed work or excessive retry key.

## Outcome

The browser requires valid mapping before submission. Malformed submitted work or an invalid retry identity reports refusal without accepting new work; row validation failures after enqueue are reported through job progress.
