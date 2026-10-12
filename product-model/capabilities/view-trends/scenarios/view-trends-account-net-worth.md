---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects financial sources and a history range for net worth.",
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
      "text": "The Product reads Account, Balance. Sum signed selected Account Balance history for account net worth; Only these account snapshots contribute to the calculation. Snapshot charts carry represented preceding snapshots and use zero before the first represented snapshot; raw currencies are not converted.",
      "kind": "product",
      "entities": [
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

# View trends account net worth

## Trigger

The User selects accounts and a history range for net worth.

## Outcome

The Product reads Account, Balance, Asset. Sum signed selected Account Balance history for account net worth; Asset entities are not included in that calculation. Snapshot charts carry represented previous values and use zero before the first represented snapshot; raw currencies are not converted.
