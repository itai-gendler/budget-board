---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a line sequence within a selected group.",
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
      "text": "The Product saves Net-worth line.Order within the selected Net-worth group and replaces that group’s Lines with the supplied list. Omitted lines and their Net-worth category entries disappear.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-line",
          "effect": "changes",
          "facts": [
            "Order"
          ],
          "as": "retained-lines"
        },
        {
          "entity": "net-worth-group",
          "effect": "changes",
          "facts": [
            "Lines"
          ]
        },
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "as": "omitted-lines"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "with": "omitted-lines"
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

# Order net worth lines save order

## Trigger

The User submits a line sequence within a selected group.

## Outcome

The Product saves Net-worth line.Order within the selected Net-worth group and replaces that group’s Lines with the supplied list. Omitted lines and their Net-worth category entries disappear.
