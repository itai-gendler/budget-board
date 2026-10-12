---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Add Group in the selected net-worth configuration.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::widget-settings"
        }
      }
    },
    {
      "text": "The Product creates Net-worth group with the next Order and empty Lines and adds it to Net-worth widget.Groups.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-group",
          "effect": "creates",
          "facts": [
            "Order",
            "Lines"
          ]
        },
        {
          "entity": "net-worth-widget",
          "effect": "changes",
          "facts": [
            "Groups"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::widget-settings"
        }
      }
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
  ]
}
---

# Add net worth group add empty group

## Trigger

The User chooses Add Group in the selected net-worth configuration.

## Outcome

The Product creates Net-worth group with the next Order and empty Lines and adds it to Net-worth widget.Groups.
