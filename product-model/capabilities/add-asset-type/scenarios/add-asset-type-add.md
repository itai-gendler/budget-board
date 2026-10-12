---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a type name and optional parent.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::asset-types"
        }
      }
    },
    {
      "text": "The Product creates Asset type with the supplied Name and validated Parent.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset-type",
          "effect": "creates",
          "facts": [
            "Name",
            "Parent"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::asset-types"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetTypeService.cs"
    }
  ]
}
---

# Add asset type add

## Trigger

The User submits a type name and optional parent.

## Outcome

The Product creates Asset type with the supplied Name and validated Parent.
