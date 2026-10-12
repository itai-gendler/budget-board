---
{
  "kind": "edge",
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
      "text": "The Product retains the configured Accounts widget and financial summaries when no visible Account or Asset sources exist; empty results do not imply removal of financial records.",
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

# View dashboard no visible data

## Trigger

The User opens the configured dashboard summaries.

## Outcome

The Product retains the configured Accounts widget and financial summaries when no visible Account or Asset sources exist; empty results do not imply removal of financial records.
