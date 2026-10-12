---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the new ordering of the financial property collection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::assets"
        }
      }
    },
    {
      "text": "The Product saves Asset.Order for the supplied ordering.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "changes",
          "facts": [
            "Order"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::assets"
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

# Order assets save order

## Trigger

The User submits the new ordering of the financial property collection.

## Outcome

The Product saves Asset.Order for the supplied ordering.
