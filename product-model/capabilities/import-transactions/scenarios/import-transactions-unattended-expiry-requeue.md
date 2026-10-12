---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "A Running import lease has expired after ten minutes with no cancellation requested.",
      "kind": "condition",
      "entities": [],
      "unattended": true,
      "contexts": {
        "web": {
          "place": "web::authenticated::import-transactions"
        }
      }
    },
    {
      "text": "After the ten-minute lease expires without cancellation, the Product returns Running Transaction import work to Pending. Started date and accumulated success/failure counts remain; stable row identities prevent ordinary replay duplication.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction-import",
          "effect": "changes",
          "facts": [
            "Status"
          ],
          "from": "Running",
          "to": "Pending"
        }
      ],
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

# Import transactions unattended expiry requeue

## Trigger

A Running import lease has expired after ten minutes with no cancellation requested.

## Outcome

After the ten-minute lease expires without cancellation, the Product returns Running Transaction import work to Pending. Started date and accumulated success/failure counts remain; stable row identities prevent ordinary replay duplication.

## Edge cases

- Expired Running work with Cancellation requested becomes Cancelled and records Completed date instead of returning to Pending.
