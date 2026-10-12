---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Add source entry for a selected line.",
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
      "text": "The Product creates Net-worth category with blank Source type, Selection method and selection and adds it to the selected Net-worth line’s Categories.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-category",
          "effect": "creates",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
          ]
        },
        {
          "entity": "net-worth-line",
          "effect": "changes",
          "facts": [
            "Categories"
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

# Add net worth category add empty source

## Trigger

The User chooses Add Category for a selected line.

## Outcome

The Product creates Net-worth category with blank Source type, Selection method and Selection value and adds it to the selected Net-worth line.Categories.
