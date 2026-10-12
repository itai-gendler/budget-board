---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses a financial property source and selects all records or an effective type.",
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
      "text": "The Product saves Net-worth category as a financial property source, selecting all records or one effective type. Rendering uses latest visible valuations for that selection.",
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

# Edit net worth category asset all or type

## Trigger

The User chooses a financial property source and selects all records or an effective type.

## Outcome

The Product saves Net-worth category as a financial property source, selecting all records or one effective type. Rendering uses latest visible valuations for that selection.
