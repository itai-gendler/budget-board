---
{
  "kind": "validation",
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
      "text": "An unknown line in the reorder list reports failure without saving the replacement list.",
      "kind": "condition",
      "entities": [],
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

# Order net worth lines unknown line

## Trigger

The User submits a line sequence within a selected group.

## Outcome

An unknown line in the reorder list reports failure without saving the replacement list.
