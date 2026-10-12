---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
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
      "target": "server/BudgetBoard.Service/TransactionService.cs#LinkTransactionsAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs#UnlinkTransactionAsync"
    }
  ]
}
---

# Transfer pairs require exact opposite amounts and unlinking retains edits

Active, unlinked, different-account records with exact nonzero opposite amounts; Transfer classification and earlier date; unlink retains edits. Candidate search windows do not become link-operation limits.
