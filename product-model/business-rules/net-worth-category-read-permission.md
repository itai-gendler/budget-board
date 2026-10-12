---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "net-worth-category",
      "effect": "reads",
      "contexts": [
        {
          "place": "web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "net-worth-line"
        },
        {
          "verb": "contains",
          "entity": "net-worth-group"
        },
        {
          "verb": "contains",
          "entity": "net-worth-widget"
        },
        {
          "verb": "owns",
          "entity": "user"
        }
      ]
    }
  ]
}
---

# Only the owning User reads Net-worth category

The owning User may read Net-worth category through the declared ownership path in the authenticated Experience.
