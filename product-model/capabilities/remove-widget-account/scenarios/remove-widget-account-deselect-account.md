---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User removes an identifier from the summary selection or clears the selection.",
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
      "text": "The Product removes the selected identifier from Accounts widget. The remaining selection limits displayed records.",
      "kind": "product",
      "entities": [
        {
          "entity": "accounts-widget",
          "effect": "changes",
          "facts": [
            "Selected accounts"
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
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    }
  ]
}
---

# Remove widget account deselect account

## Trigger

The User removes an identifier from the summary selection or clears the selection.

## Outcome

The Product removes the selected identifier from Accounts widget. The remaining selection limits displayed records.
