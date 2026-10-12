---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes built-in financial property type availability.",
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
      "text": "The Product disables the built-in vocabulary in User settings, clears dependent selections and unparents custom Asset type entries referencing the disabled vocabulary.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Built-in asset types disabled"
          ]
        },
        {
          "entity": "asset-type",
          "effect": "changes",
          "facts": [
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

# Change asset types settings disable builtin

## Trigger

The User changes built-in financial property type availability.

## Outcome

The Product disables the built-in vocabulary in User settings, clears dependent selections and unparents custom Asset type entries referencing the disabled vocabulary.
