---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses the Metric summary and submits Add.",
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
      "text": "The Product creates Metric widget with the shipped This Month’s Spending title, current-month expense-sum expression and total expenses label.",
      "kind": "product",
      "entities": [
        {
          "entity": "metric-widget",
          "effect": "creates",
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

# Add widget metric

## Trigger

The User chooses the Metric summary and submits Add.

## Outcome

The Product creates Metric widget with the shipped This Month’s Spending title, current-month expense-sum expression and total expenses label.
