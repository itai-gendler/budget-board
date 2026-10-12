---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects Net cash flow and the analysis period.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::trends"
        }
      }
    },
    {
      "text": "The Product reads Transaction. Aggregate signed Transaction amounts into monthly net cash flow. Raw currencies are not converted.",
      "kind": "product",
      "entities": [
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
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::trends"
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
      "target": "client/src/app/Authorized/PageContent/Trends/Trends.tsx"
    }
  ]
}
---

# View trends net cash flow

## Trigger

The User selects Net cash flow and the analysis period.

## Outcome

The Product reads Transaction. Aggregate signed Transaction amounts into monthly net cash flow. Raw currencies are not converted.
