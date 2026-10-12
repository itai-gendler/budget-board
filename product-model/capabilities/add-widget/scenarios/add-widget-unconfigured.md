---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Spending trends or uncategorized activity and submits Add.",
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
      "text": "The Product creates Dashboard widget with the selected unconfigured Kind.",
      "kind": "product",
      "entities": [
        {
          "entity": "dashboard-widget",
          "effect": "creates",
          "facts": [
            "Kind"
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

# Add widget unconfigured

## Trigger

The User chooses Spending trends or uncategorized activity and submits Add.

## Outcome

The Product creates Dashboard widget of the selected Kind, either Spending trends or Uncategorized transactions, without additional stored configuration.
