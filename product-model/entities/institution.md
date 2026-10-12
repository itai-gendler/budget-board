---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/InstitutionService.cs"
    }
  ],
  "relations": [
    {
      "entity": "account",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Institution

Active, Deleted. Account creation/restoration can restore it; deleting its last active Account can mark it deleted.

## Information kept

- **Name** — Name used to present or select this instance.
- **Order** — Retained position in the corresponding collection.
- **Deletion date** — Soft-deletion marker retained for recovery.

## States

### Active

No deletion date is recorded.

### Deleted

The instance retains its soft-deletion marker.
