---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a line name and position in the selected group.",
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
      "text": "When the requested group position is missing, the Product creates Net-worth group with that Order and the new Net-worth line; the new group joins Net-worth widget.Groups.",
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
          "entity": "net-worth-line",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ],
          "with": "net-worth-group"
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
      "target": "server/BudgetBoard.Service/NetWorthWidgetLineService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/widgets.ts"
    }
  ]
}
---

# Add net worth line create missing group

## Trigger

The User submits a line name and position in the selected group.

## Outcome

When the requested group position is missing, the Product creates Net-worth group with that Order and the new Net-worth line; the new group joins Net-worth widget.Groups.
