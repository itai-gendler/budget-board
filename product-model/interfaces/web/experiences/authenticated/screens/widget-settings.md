---
{
  "entities": [
    {
      "entity": "accounts-widget",
      "shows": [
        "Selected accounts"
      ],
      "collects": [
        "Selected accounts"
      ]
    },
    {
      "entity": "flows-widget",
      "shows": [
        "Month count"
      ],
      "collects": [
        "Month count"
      ]
    },
    {
      "entity": "metric-widget",
      "shows": [
        "Title",
        "Value template",
        "Label template"
      ],
      "collects": [
        "Title",
        "Value template",
        "Label template"
      ]
    },
    {
      "entity": "net-worth-widget",
      "shows": [
        "Groups"
      ],
      "collects": [
        "Groups"
      ]
    },
    {
      "entity": "net-worth-group",
      "shows": [
        "Order",
        "Lines"
      ],
      "collects": [
        "Order",
        "Lines"
      ]
    },
    {
      "entity": "net-worth-line",
      "shows": [
        "Name",
        "Order",
        "Categories"
      ],
      "collects": [
        "Name",
        "Order",
        "Categories"
      ]
    },
    {
      "entity": "net-worth-category",
      "shows": [
        "Source type",
        "Selection method",
        "Selection value"
      ],
      "collects": [
        "Source type",
        "Selection method",
        "Selection value"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name",
        "Type"
      ]
    },
    {
      "entity": "institution",
      "shows": [
        "Name"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/widgets.ts"
    }
  ]
}
---

# Widget settings

One selected widget’s configuration. Shows and collects account selection, Flows month count, Metric templates, net-worth Groups, Lines and Categories.
