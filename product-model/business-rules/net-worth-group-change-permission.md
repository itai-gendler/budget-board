---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "net-worth-group",
      "effect": "changes",
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

# Only the owning User changes Net-worth group

The owning User may change Net-worth group through the declared ownership path in the authenticated Experience.
