---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects Spending categories and the analysis period.",
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
      "text": "The Product reads Transaction, Category. Aggregate expense spending by effective Category for the selected period. Raw currencies are not converted.",
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

# View trends spending categories

## Trigger

The User selects Spending categories and the analysis period.

## Outcome

The Product reads Transaction, Category. Aggregate expense spending by effective Category for the selected period. Raw currencies are not converted.
