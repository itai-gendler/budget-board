---
{
  "kind": "validation",
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
      "text": "Reenabling a built-in vocabulary with conflicting custom names is refused; the selected setting remains.",
      "kind": "condition",
      "entities": [],
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

# Change asset types settings custom name conflict

## Trigger

The User changes built-in financial property type availability.

## Outcome

Reenabling a built-in vocabulary with conflicting custom names is refused; the selected setting remains.
