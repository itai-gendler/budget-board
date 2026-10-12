---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects property records and a valuation history range.",
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
      "text": "The Product reads Asset, Value. Present selected Asset Value history over the chosen range. Snapshot charts carry represented previous values and use zero before the first represented snapshot; raw currencies are not converted.",
      "kind": "product",
      "entities": [
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

# View trends asset values

## Trigger

The User selects property records and a valuation history range.

## Outcome

The Product reads Asset, Value. Present selected Asset Value history over the chosen range. Snapshot charts carry represented previous values and use zero before the first represented snapshot; raw currencies are not converted.
