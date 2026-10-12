---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    }
  ],
  "relations": [
    {
      "entity": "tag",
      "verb": "has",
      "cardinality": "many-to-many"
    },
    {
      "entity": "transaction",
      "verb": "links",
      "cardinality": "one-to-one"
    }
  ]
}
---

# Transaction

A financial activity record with signed amount, classification, notes, source, tag memberships and optional recurring or transfer association.

## Information kept

- **Date** — Calendar date of the record.
- **Merchant** — Description or recurring merchant criterion.
- **Amount** — Signed monetary amount.
- **Category** — Parent transaction-category name.
- **Subcategory** — Leaf transaction-category name.
- **Notes** — Free-text notes.
- **Source** — Manual or provider origin classification.
- **Provider reference** — Provider record reference used for matching and duplicate avoidance.
- **Deletion date** — Soft-deletion marker retained for recovery.
- **Tags** — Assigned Tag memberships.
- **Recurring assignment** — Associated recurring definition, when any.
- **Transfer counterpart** — Linked opposite transaction, when any.

## States

### Active

No deletion date is recorded.

### Deleted

The instance retains its soft-deletion marker.
