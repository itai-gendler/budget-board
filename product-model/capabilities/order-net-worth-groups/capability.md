---
{
  "availability": [
    {
      "place": "web::authenticated"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/NetWorthWidgetGroupService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/widgets.ts"
    }
  ],
  "domain": "dashboard"
}
---

# Order net worth groups

Replace the widget’s group sequence with the supplied ordered list, removing omitted groups and their contained entries.
