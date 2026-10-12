---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the Metric title and both templates.",
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
      "text": "The Product saves Metric widget Title and both templates. Expressions are evaluated when displayed; saving does not validate every expression.",
      "kind": "product",
      "entities": [
        {
          "entity": "metric-widget",
          "effect": "changes",
          "facts": [
            "Title",
            "Value template",
            "Label template"
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

# Edit widget metric template

## Trigger

The User submits the Metric title and both templates.

## Outcome

The Product saves Metric widget Title and both templates. Expressions are evaluated when displayed; saving does not validate every expression.
