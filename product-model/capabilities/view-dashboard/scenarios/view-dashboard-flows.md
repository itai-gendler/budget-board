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
      "text": "Flows widget nets signed Transaction leaf totals across its Month count, omits net-zero groups and derives Cash available, surplus and deficit as chart aggregates.",
      "kind": "product",
      "entities": [
        {
          "entity": "flows-widget",
          "effect": "reads",
          "facts": [
            "Month count"
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
          "entity": "category",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent",
            "Classification"
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

# View dashboard flows

## Trigger

The User opens the configured dashboard summaries.

## Outcome

Flows widget nets signed Transaction leaf totals across its Month count, omits net-zero groups and derives Cash available, surplus and deficit as chart aggregates.
