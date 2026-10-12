---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement name for the selected line.",
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
      "text": "The Product saves Net-worth line.Name. Name-based net-worth source entry references are not repaired; duplicate names are not universally rejected.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-line",
          "effect": "changes",
          "facts": [
            "Name"
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

# Edit net worth line rename

## Trigger

The User submits a replacement name for the selected line.

## Outcome

The Product saves Net-worth line.Name. Name-based Net-worth category references are not repaired; duplicate names are not universally rejected.
