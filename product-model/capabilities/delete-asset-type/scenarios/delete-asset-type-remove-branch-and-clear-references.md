---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected financial property type branch.",
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
      "text": "The Product removes the Asset type branch and clears matching Asset.Type selections.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset-type",
          "effect": "removes"
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

# Delete asset type remove branch and clear references

## Trigger

The User confirms removal of the selected financial property type branch.

## Outcome

The Product removes the Asset type branch and clears matching Asset.Type selections.
