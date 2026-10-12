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
      "text": "The Product reenables the built-in vocabulary through User settings after checking custom-name conflicts.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Built-in asset types disabled"
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

# Change asset types settings enable builtin

## Trigger

The User changes built-in financial property type availability.

## Outcome

The Product reenables the built-in vocabulary through User settings after checking custom-name conflicts.
