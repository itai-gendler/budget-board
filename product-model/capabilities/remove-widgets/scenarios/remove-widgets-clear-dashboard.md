---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms clearing all dashboard summaries.",
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
      "text": "The Product removes all selected dashboard instances after confirmation from the appropriate Dashboard widget, Accounts widget, Flows widget, Metric widget or Net-worth widget family. Removing net-worth configuration removes contained Net-worth group, Net-worth line and Net-worth category entries. Financial records remain.",
      "kind": "product",
      "entities": [
        {
          "entity": "dashboard-widget",
          "effect": "removes"
        },
        {
          "entity": "accounts-widget",
          "effect": "removes"
        },
        {
          "entity": "flows-widget",
          "effect": "removes"
        },
        {
          "entity": "metric-widget",
          "effect": "removes"
        },
        {
          "entity": "net-worth-widget",
          "effect": "removes"
        },
        {
          "entity": "net-worth-group",
          "effect": "removes",
          "with": "net-worth-widget"
        },
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "with": "net-worth-group"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "with": "net-worth-line"
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

# Remove widgets clear dashboard

## Trigger

The User confirms clearing all dashboard summaries.

## Outcome

The Product removes all selected dashboard instances after confirmation from the appropriate Dashboard widget, Accounts widget, Flows widget, Metric widget or Net-worth widget family. Removing net-worth configuration removes contained Net-worth group, Net-worth line and Net-worth category entries. Financial records remain.
