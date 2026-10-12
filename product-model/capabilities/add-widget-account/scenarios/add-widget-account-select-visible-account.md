---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects a visible source to add to the summary selection.",
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
      "text": "The Product adds the selected visible Account to Accounts widget. The browser offers only otherwise-visible records for selection.",
      "kind": "product",
      "entities": [
        {
          "entity": "accounts-widget",
          "effect": "changes",
          "facts": [
            "Selected accounts"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
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
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    }
  ]
}
---

# Add widget account select visible account

## Trigger

The User selects a visible account to add to the summary selection.

## Outcome

The Product adds the selected visible Account to Accounts widget. The browser offers only otherwise-visible records for selection.
