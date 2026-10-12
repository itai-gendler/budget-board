---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the configured dashboard summaries.",
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
      "text": "The Product presents six shipped summaries: Accounts widget, Dashboard widget Uncategorized transactions and Spending trends, Net-worth widget, Metric widget and Flows widget.",
      "kind": "product",
      "entities": [
        {
          "entity": "accounts-widget",
          "effect": "reads",
          "facts": [
            "Selected accounts"
          ]
        },
        {
          "entity": "dashboard-widget",
          "effect": "reads",
          "facts": [
            "Kind"
          ]
        },
        {
          "entity": "net-worth-widget",
          "effect": "reads",
          "facts": [
            "Groups"
          ]
        },
        {
          "entity": "metric-widget",
          "effect": "reads",
          "facts": [
            "Title",
            "Value template",
            "Label template"
          ]
        },
        {
          "entity": "flows-widget",
          "effect": "reads",
          "facts": [
            "Month count"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name",
            "Type",
            "Interest rate",
            "Source",
            "Account hidden",
            "Transactions hidden",
            "Order",
            "Deletion date"
          ]
        },
        {
          "entity": "institution",
          "effect": "reads",
          "facts": [
            "Name",
            "Order",
            "Deletion date"
          ]
        },
        {
          "entity": "balance",
          "effect": "reads",
          "facts": [
            "Date",
            "Amount"
          ]
        },
        {
          "entity": "transaction",
          "effect": "reads",
          "facts": [
            "Date",
            "Merchant",
            "Amount",
            "Category",
            "Subcategory",
            "Notes",
            "Source",
            "Provider reference",
            "Deletion date",
            "Tags",
            "Recurring assignment",
            "Transfer counterpart"
          ]
        },
        {
          "entity": "asset",
          "effect": "reads",
          "facts": [
            "Name",
            "Type",
            "Purchase date",
            "Purchase price",
            "Sale date",
            "Sale price",
            "Hidden",
            "Order",
            "Deletion date"
          ]
        },
        {
          "entity": "value",
          "effect": "reads",
          "facts": [
            "Date",
            "Amount"
          ]
        },
        {
          "entity": "budget",
          "effect": "reads",
          "facts": [
            "Category",
            "Month",
            "Limit",
            "Rollover start"
          ]
        },
        {
          "entity": "goal",
          "effect": "reads",
          "facts": [
            "Name",
            "Target",
            "Initial amount",
            "Selected accounts",
            "Stored contribution",
            "Stored target date",
            "Completed date"
          ]
        },
        {
          "entity": "net-worth-group",
          "effect": "reads",
          "facts": [
            "Order",
            "Lines"
          ]
        },
        {
          "entity": "net-worth-line",
          "effect": "reads",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ]
        },
        {
          "entity": "net-worth-category",
          "effect": "reads",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
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
      "target": "client/src/helpers/charts.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/metricWidget.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Dashboard/Dashboard.tsx"
    }
  ]
}
---

# View dashboard default widgets

## Trigger

The User opens the configured dashboard summaries.

## Outcome

The Product presents six shipped summaries: Accounts widget, Dashboard widget Uncategorized transactions and Spending trends, Net-worth widget, Metric widget and Flows widget.
