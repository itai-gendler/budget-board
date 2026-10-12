---
{
  "kind": "primary",
  "routes": {
    "assets": "Assets",
    "asset-details": "Asset details"
  },
  "steps": [
    {
      "text": "The User opens the active collection and selects a record to inspect dated valuation history.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "assets": {
          "place": "web::authenticated::assets"
        },
        "asset-details": {
          "place": "web::authenticated::asset-details"
        }
      }
    },
    {
      "text": "The Product presents active Asset facts and latest Value amounts; details expose dated history.",
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
        "assets": {
          "place": "web::authenticated::assets"
        },
        "asset-details": {
          "place": "web::authenticated::asset-details"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetService.cs"
    }
  ]
}
---

# Browse assets active collection and detail

## Trigger

The User opens the active collection and selects a record to inspect dated valuation history.

## Outcome

The Product presents active Asset facts and latest Value amounts; details expose dated history.
