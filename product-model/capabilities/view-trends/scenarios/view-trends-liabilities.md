---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects liability-classified sources and a history range.",
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
      "text": "The Product reads Account, Account type, Balance. Present selected liability-classified Account Balance history using effective custom and built-in classifications. Snapshot charts carry represented preceding snapshots and use zero before the first represented snapshot; raw currencies are not converted.",
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
          "entity": "account-type",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent",
            "Classification"
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

# View trends liabilities

## Trigger

The User selects liability-classified accounts and a history range.

## Outcome

The Product reads Account, Account type, Balance. Present selected liability-classified Account Balance history using effective custom and built-in classifications. Snapshot charts carry represented previous values and use zero before the first represented snapshot; raw currencies are not converted.
