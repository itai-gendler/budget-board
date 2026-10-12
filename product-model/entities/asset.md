---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetService.cs"
    }
  ],
  "relations": [
    {
      "entity": "value",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Asset

A financial asset with acquisition/disposal information and dated valuations, retained after deletion and recoverable.

## Information kept

- **Name** — Name used to present or select this instance.
- **Type** — Selected financial type name.
- **Purchase date** — Recorded acquisition date, when supplied.
- **Purchase price** — Recorded acquisition price, when supplied.
- **Sale date** — Recorded disposal date, when supplied.
- **Sale price** — Recorded disposal price, when supplied.
- **Hidden** — Whether Asset summaries omit this Asset.
- **Order** — Retained position in the corresponding collection.
- **Deletion date** — Soft-deletion marker retained for recovery.

## States

### Active

No deletion date is recorded.

### Deleted

The instance retains its soft-deletion marker.
