---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction-import",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
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

# Import cancellation and lease expiry preserve completed work

Pending cancellation immediate; Running cancellation after a batch. Ten-minute lease recovery can requeue/cancel work. Owned retry key returns existing work; replay can inflate counters.
