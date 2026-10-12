---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the group sequence for the selected net-worth configuration.",
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
      "text": "The Product assigns Net-worth group.Order in the submitted sequence and replaces Net-worth widget.Groups with that supplied list. Omitted groups and their Net-worth line and Net-worth category entries are removed.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-group",
          "effect": "changes",
          "facts": [
            "Order"
          ],
          "as": "retained-groups"
        },
        {
          "entity": "net-worth-widget",
          "effect": "changes",
          "facts": [
            "Groups"
          ]
        },
        {
          "entity": "net-worth-group",
          "effect": "removes",
          "as": "omitted-groups"
        },
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "with": "omitted-groups"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "with": "net-worth-line"
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

# Order net worth groups save order

## Trigger

The User submits the group sequence for the selected net-worth configuration.

## Outcome

The Product assigns Net-worth group.Order in the submitted sequence and replaces Net-worth widget.Groups with that supplied list. Omitted groups and their Net-worth line and Net-worth category entries are removed.
