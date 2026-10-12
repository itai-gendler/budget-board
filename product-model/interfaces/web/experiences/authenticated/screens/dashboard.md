---
{
  "entities": [
    {
      "entity": "account",
      "shows": [
        "Name"
      ]
    },
    {
      "entity": "institution",
      "shows": [
        "Name"
      ]
    },
    {
      "entity": "balance",
      "shows": [
        "Date",
        "Amount"
      ]
    },
    {
      "entity": "transaction",
      "shows": [
        "Date",
        "Merchant",
        "Amount",
        "Category",
        "Subcategory",
        "Notes",
        "Tags",
        "Recurring assignment",
        "Transfer counterpart"
      ]
    },
    {
      "entity": "asset",
      "shows": [
        "Name"
      ]
    },
    {
      "entity": "value",
      "shows": [
        "Date",
        "Amount"
      ]
    },
    {
      "entity": "category",
      "shows": [
        "Name",
        "Parent",
        "Classification"
      ]
    },
    {
      "entity": "dashboard-widget",
      "shows": [
        "Kind"
      ]
    },
    {
      "entity": "flows-widget",
      "shows": [
        "Month count"
      ]
    },
    {
      "entity": "metric-widget",
      "shows": [
        "Title"
      ]
    },
    {
      "entity": "net-worth-widget",
      "shows": [
        "Groups"
      ]
    },
    {
      "entity": "net-worth-group",
      "shows": [
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
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Dashboard/Dashboard.tsx"
    }
  ]
}
---

# Dashboard

Widget collection and financial summaries. Shows widget configuration, Account/Institution names, dated amounts and relevant Transaction facts.

## Financial results

Configured Metric expressions present their calculated Budget and Goal results; these results use the source-specific Rules. Metric expressions themselves are edited at Widget settings.
