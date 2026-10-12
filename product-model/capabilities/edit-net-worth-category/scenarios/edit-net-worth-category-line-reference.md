---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses a line-name source and submits the referenced name.",
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
      "text": "The Product saves Net-worth category as a line-name source. Rendering recursively sums the sources of the matching name. Renames leave references unchanged and overlapping sources may count amounts repeatedly.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-category",
          "effect": "changes",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
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
      "target": "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/widgets.ts"
    }
  ]
}
---

# Edit net worth category line reference

## Trigger

The User chooses a line-name source and submits the referenced name.

## Outcome

The Product saves Net-worth category as a line-name source. Rendering recursively sums the sources of the matching name. Renames leave references unchanged and overlapping sources may count amounts repeatedly.
