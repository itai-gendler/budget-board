---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to the selected type’s name or parent.",
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
      "text": "The Product changes Asset type Name and Parent; matching Asset type selections and child parent names follow the rename.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset-type",
          "effect": "changes",
          "facts": [
            "Name",
            "Parent"
          ]
        },
        {
          "entity": "asset",
          "effect": "changes",
          "facts": [
            "Type"
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

# Edit asset type rename

## Trigger

The User submits changes to the selected type’s name or parent.

## Outcome

The Product changes Asset type Name and Parent; matching Asset type selections and child parent names follow the rename.
