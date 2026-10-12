---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User enters a name and submits creation of the financial property record.",
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
      "text": "The Product creates Asset with Name, empty Type, absent purchase/sale facts, visible selection, initial Order and no deletion marker.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "creates",
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
          ],
          "to": "Active"
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

# Add asset add

## Trigger

The User enters a name and submits creation of the financial property record.

## Outcome

The Product creates Asset with Name, empty Type, absent purchase/sale facts, visible selection, initial Order and no deletion marker.
