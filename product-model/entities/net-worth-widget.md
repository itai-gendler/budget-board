---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    }
  ],
  "relations": [
    {
      "entity": "net-worth-group",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "dashboard"
}
---

# Net-worth widget

Created, reset and removed.

## Information kept

- **Groups** — Contained ordered net-worth Groups.
