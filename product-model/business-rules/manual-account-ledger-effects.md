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
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs#CreateTransactionAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs#UpdateTransactionsAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs#RestoreTransactionsAsync"
    }
  ]
}
---

# Manual Account source determines monetary ledger effects

Manual Account source controls dated balance creation and adjustments, including edit reversal, deletion and restoration. Creation adds signed amount to snapshots on/after the date, creating a missing dated snapshot from the preceding balance or zero. Editing reverses the old amount/date contribution and applies the new one. Deletion subtracts and restoration adds. Repeated deletion/restoration is not generally state-guarded. The Account source controls these effects even when an imported Transaction has Manual source.
