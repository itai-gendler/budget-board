---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/NetWorthWidgetGroupService.cs"
    }
  ],
  "relations": [
    {
      "entity": "net-worth-line",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "dashboard"
}
---

# Net-worth group

Independently addressed; created/reordered and removed by configuration replacement or cleanup.

## Information kept

- **Order** — Retained position in the corresponding collection.
- **Lines** — Contained ordered net-worth Lines.
