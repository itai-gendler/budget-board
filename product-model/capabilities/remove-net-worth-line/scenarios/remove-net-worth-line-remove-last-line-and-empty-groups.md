---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of a selected line.",
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
      "text": "The Product removes the selected Net-worth line and its Net-worth category entries, removes all now-empty Net-worth group instances and changes Net-worth widget.Groups.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "with": "net-worth-group"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "with": "net-worth-line"
        },
        {
          "entity": "net-worth-group",
          "effect": "removes"
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

# Remove net worth line remove last line and empty groups

## Trigger

The User confirms removal of a selected line.

## Outcome

The Product removes the selected Net-worth line and its Net-worth category entries, removes all now-empty Net-worth group instances and changes Net-worth widget.Groups.
