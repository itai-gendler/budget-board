---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Remove for the selected net-worth source entry.",
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
      "text": "The Product removes the selected Net-worth category and updates Net-worth line.Categories. An unknown source-entry identifier can leave the list unchanged.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-category",
          "effect": "removes"
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

# Remove net worth category remove

## Trigger

The User chooses Remove for the selected net-worth source entry.

## Outcome

The Product removes the selected Net-worth category and updates Net-worth line.Categories. An unknown source-entry identifier can leave the list unchanged.
