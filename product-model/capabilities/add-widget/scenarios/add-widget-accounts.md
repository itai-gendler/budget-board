---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses the financial-record summary and submits Add.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "The Product creates Accounts widget with an empty selection; it displays all otherwise-visible records.",
      "kind": "product",
      "entities": [
        {
          "entity": "accounts-widget",
          "effect": "creates",
          "facts": [
            "Selected accounts"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
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

# Add widget accounts

## Trigger

The User chooses the financial-record summary and submits Add.

## Outcome

The Product creates Accounts widget with an empty selection; it displays all otherwise-visible records.
