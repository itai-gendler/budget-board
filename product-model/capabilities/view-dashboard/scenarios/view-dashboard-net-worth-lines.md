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
      "text": "Net-worth widget renders ordered Net-worth group and Net-worth line sources configured by Net-worth category. Visible Account Balance and Asset Value sources and recursive line-name references may overlap rather than reserve funds.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-widget",
          "effect": "reads",
          "facts": [
            "Groups"
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
          "entity": "balance",
          "effect": "reads",
          "facts": [
            "Date",
            "Amount"
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
          "entity": "account-type",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent",
            "Classification"
          ]
        },
        {
          "entity": "asset-type",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent"
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

# View dashboard net worth lines

## Trigger

The User opens the configured dashboard summaries.

## Outcome

Net-worth widget renders ordered Net-worth group and Net-worth line sources configured by Net-worth category. Visible Account Balance and Asset Value sources and recursive line-name references may overlap rather than reserve funds.
