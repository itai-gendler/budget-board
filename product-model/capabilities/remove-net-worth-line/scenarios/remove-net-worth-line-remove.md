---
{
  "kind": "primary",
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
      "text": "The Product removes Net-worth line and its contained Net-worth category entries and updates Net-worth group.Lines.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-line",
          "effect": "removes"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "with": "net-worth-line"
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

# Remove net worth line remove

## Trigger

The User confirms removal of a selected line.

## Outcome

The Product removes Net-worth line and its contained Net-worth category entries and updates Net-worth group.Lines.
