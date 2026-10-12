---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "institution",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "asset",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "recurring-transaction",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "goal",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs#DeleteAccountAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs#RestoreAccountAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs#PermanentlyDeleteAccountAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs#DeleteTransactionsAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Database/Data/UserDataContext.cs#OnModelCreating"
    }
  ]
}
---

# Deletion and restoration retain their operation-specific metadata losses

Web Account restoration leaves Transactions deleted. Metadata losses remain. Permanent Account removal requires prior deletion and does not rebase Goals. Account soft deletion clears Type, detaches provider links and returns Source to Manual; the last active Account can mark its Institution deleted and reset its Order to zero. Restoration changes Account and Institution deletion markers only. Asset deletion retains Values and clears Type; recovery does not restore Type. Ordinary Transaction deletion clears Category, Subcategory, Tags and transfer links. Permanent Account removal removes retained snapshots, Transactions and recurring definitions; Goal membership can disappear without baseline rebasing.
