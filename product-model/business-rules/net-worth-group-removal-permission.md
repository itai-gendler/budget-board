---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "net-worth-group",
      "effect": "removes",
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
      "target": "server/BudgetBoard.Service/NetWorthWidgetGroupService.cs"
    }
  ],
  "permits": [
    {
      "related": [
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

# Only the owning User removes Net-worth group

The owning User may remove Net-worth group through the declared ownership path in the authenticated Experience.
