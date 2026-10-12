---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses a financial-record type source and submits the effective type selection.",
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
      "text": "The Product saves Net-worth category as a financial-record type source. Rendering uses visible latest amounts for the selected effective type and its children.",
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

# Edit net worth category account type

## Trigger

The User chooses a financial-record type source and submits the effective type selection.

## Outcome

The Product saves Net-worth category as a financial-record type source. Rendering uses visible latest amounts for the selected effective type and its children.
