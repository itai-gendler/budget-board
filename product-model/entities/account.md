---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs#AccountService"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Database/Data/UserDataContext.cs#OnModelCreating"
    }
  ],
  "relations": [
    {
      "entity": "balance",
      "verb": "contains",
      "cardinality": "one-to-many"
    },
    {
      "entity": "transaction",
      "verb": "contains",
      "cardinality": "one-to-many"
    },
    {
      "entity": "recurring-transaction",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Account

A financial account with dated balances and transaction history, retained after soft deletion until permanently removed.

## Information kept

- **Name** — Name used to present or select this instance.
- **Type** — Selected financial type name.
- **Interest rate** — Account rate used in Goal interest estimates.
- **Source** — Manual or provider origin classification.
- **Account hidden** — Whether account-based summaries omit this Account.
- **Transactions hidden** — Whether transaction-based views and processing omit its records.
- **Order** — Retained position in the corresponding collection.
- **Deletion date** — Soft-deletion marker retained for recovery.

## States

### Active

No deletion date is recorded.

### Deleted

The instance retains its soft-deletion marker.
