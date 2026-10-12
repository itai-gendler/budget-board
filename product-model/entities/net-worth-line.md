---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/NetWorthWidgetLineService.cs"
    }
  ],
  "relations": [
    {
      "entity": "net-worth-category",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "dashboard"
}
---

# Net-worth line

Independently addressed; created, renamed, reordered and removed.

## Information kept

- **Name** — Name used to present or select this instance.
- **Order** — Retained position in the corresponding collection.
- **Categories** — Contained net-worth source entries.
