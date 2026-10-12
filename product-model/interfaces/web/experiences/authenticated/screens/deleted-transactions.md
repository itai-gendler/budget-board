---
{
  "entities": [
    {
      "entity": "transaction",
      "shows": [
        "Merchant",
        "Deletion date"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Transactions/TransactionsSettings/DeletedTransactions/DeletedTransactionCards/DeletedTransactionCard/DeletedTransactionsCard.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Transactions/TransactionsSettings/DeletedTransactions/DeletedTransactionCards/DeletedTransactionCard/DeletedTransactionsCard.tsx#DeletedTransactionsCard"
    }
  ]
}
---

# Deleted transactions

Retained merchant names and time since deletion identify records available for restoration.
