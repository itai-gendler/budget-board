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
      "target": "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs"
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

# Edit net worth category

Choose Account-type, Asset-all/type or line-name sources for a net-worth entry; recursive sources retain name dependence and differing cycle checks.
