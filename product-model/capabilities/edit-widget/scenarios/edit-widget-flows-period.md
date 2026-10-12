---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a Flows month count from one through twelve.",
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
      "text": "The Product saves Flows widget.Month count from one through twelve.",
      "kind": "product",
      "entities": [
        {
          "entity": "flows-widget",
          "effect": "changes",
          "facts": [
            "Month count"
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

# Edit widget flows period

## Trigger

The User submits a Flows month count from one through twelve.

## Outcome

The Product saves Flows widget.Month count from one through twelve.
