---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs#SplitTransactionAsync"
    }
  ]
}
---

# Splitting preserves signed total under the linked-record and magnitude checks

Linked records cannot split; strict magnitude bound and preserved total; no separate server same-sign promise.
