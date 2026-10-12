---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms Reset Dashboard to restore the shipped summaries.",
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
      "text": "The Product removes existing Dashboard widget, Accounts widget, Flows widget, Metric widget and Net-worth widget instances with Net-worth group, Net-worth line and Net-worth category entries, then creates six shipped default summaries and their configuration.",
      "kind": "product",
      "entities": [
        {
          "entity": "dashboard-widget",
          "effect": "removes",
          "as": "old-dashboard-widget"
        },
        {
          "entity": "accounts-widget",
          "effect": "removes",
          "as": "old-accounts-widget"
        },
        {
          "entity": "flows-widget",
          "effect": "removes",
          "as": "old-flows-widget"
        },
        {
          "entity": "metric-widget",
          "effect": "removes",
          "as": "old-metric-widget"
        },
        {
          "entity": "net-worth-widget",
          "effect": "removes",
          "as": "old-net-worth-widget"
        },
        {
          "entity": "net-worth-group",
          "effect": "removes",
          "as": "old-groups",
          "with": "old-net-worth-widget"
        },
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "as": "old-lines",
          "with": "old-groups"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "as": "old-categories",
          "with": "old-lines"
        },
        {
          "entity": "dashboard-widget",
          "effect": "creates",
          "facts": [
            "Kind"
          ],
          "as": "uncategorized"
        },
        {
          "entity": "dashboard-widget",
          "effect": "creates",
          "facts": [
            "Kind"
          ],
          "as": "spending"
        },
        {
          "entity": "accounts-widget",
          "effect": "creates",
          "facts": [
            "Selected accounts"
          ],
          "as": "existing-accounts-widget"
        },
        {
          "entity": "flows-widget",
          "effect": "creates",
          "facts": [
            "Month count"
          ],
          "as": "existing-flows-widget"
        },
        {
          "entity": "metric-widget",
          "effect": "creates",
          "facts": [
            "Title",
            "Value template",
            "Label template"
          ],
          "as": "existing-metric-widget"
        },
        {
          "entity": "net-worth-widget",
          "effect": "creates",
          "facts": [
            "Groups"
          ],
          "as": "existing-net-worth-widget"
        },
        {
          "entity": "net-worth-group",
          "effect": "creates",
          "facts": [
            "Order",
            "Lines"
          ],
          "with": "existing-net-worth-widget",
          "as": "existing-net-worth-group"
        },
        {
          "entity": "net-worth-line",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ],
          "with": "existing-net-worth-group",
          "as": "existing-net-worth-line"
        },
        {
          "entity": "net-worth-category",
          "effect": "creates",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
          ],
          "with": "existing-net-worth-line",
          "as": "existing-net-worth-category"
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

# Reset dashboard replace with defaults

## Trigger

The User confirms Reset Dashboard to restore the shipped summaries.

## Outcome

The Product removes existing Dashboard widget, Accounts widget, Flows widget, Metric widget and Net-worth widget instances with Net-worth group, Net-worth line and Net-worth category entries, then creates six shipped default summaries and their configuration.
