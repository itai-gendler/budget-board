---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the deleted property collection to inspect retained names and deletion dates.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-assets"
        }
      }
    },
    {
      "text": "The Product presents retained Asset names and deletion markers for recovery.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "reads",
          "facts": [
            "Name",
            "Deletion date"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-assets"
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

# Browse assets deleted collection

## Trigger

The User opens the deleted property collection to inspect retained names and deletion dates.

## Outcome

The Product presents retained Asset names and deletion markers for recovery.
