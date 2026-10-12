---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User removes the final identifier from the configured summary selection.",
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
      "text": "The Product clears the selection in Accounts widget. Empty selection displays all otherwise-visible records, including after the final selected identifier is removed.",
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

# Remove widget account last selection means all

## Trigger

The User removes the final identifier from the configured summary selection.

## Outcome

The Product clears the selection in Accounts widget. Empty selection displays all otherwise-visible records, including after the final selected identifier is removed.
