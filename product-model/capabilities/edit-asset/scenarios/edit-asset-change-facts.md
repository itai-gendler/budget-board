---
{
  "kind": "primary",
  "routes": {
    "assets": "Assets",
    "asset-details": "Asset details"
  },
  "steps": [
    {
      "text": "The User submits changes to name, type, purchase date/price or sale date/price.",
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
      "text": "The Product saves Asset Name, Type and purchase/sale facts; these changes create no financial ledger entries.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "changes",
          "facts": [
            "Name",
            "Type",
            "Purchase date",
            "Purchase price",
            "Sale date",
            "Sale price"
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

# Edit asset change facts

## Trigger

The User submits changes to name, type, purchase date/price or sale date/price.

## Outcome

The Product saves Asset Name, Type and purchase/sale facts; these changes create no financial ledger entries.
