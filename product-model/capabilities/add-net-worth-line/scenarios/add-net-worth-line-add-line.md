---
{
  "kind": "primary",
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
      "text": "The Product creates Net-worth line with supplied Name and Order and empty Categories, and appends it to Net-worth group.Lines.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-line",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ]
        },
        {
          "entity": "net-worth-group",
          "effect": "changes",
          "facts": [
            "Lines"
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

# Add net worth line add line

## Trigger

The User submits a line name and position in the selected group.

## Outcome

The Product creates Net-worth line with supplied Name and Order and empty Categories, and appends it to Net-worth group.Lines.
