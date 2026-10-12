---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses the Flows summary and submits Add.",
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
      "text": "The Product creates Flows widget with Month count one.",
      "kind": "product",
      "entities": [
        {
          "entity": "flows-widget",
          "effect": "creates",
          "facts": [
            "Month count"
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

# Add widget flows

## Trigger

The User chooses the Flows summary and submits Add.

## Outcome

The Product creates Flows widget with Month count one.
