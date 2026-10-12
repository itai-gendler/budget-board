---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the effective financial property type vocabulary.",
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
      "text": "The Product presents the effective built-in vocabulary and custom Asset type facts, respecting User settings built-in availability.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset-type",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent"
          ]
        },
        {
          "entity": "user-settings",
          "effect": "reads",
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

# Browse asset types builtin and custom

## Trigger

The User opens the effective financial property type vocabulary.

## Outcome

The Product presents the effective built-in vocabulary and custom Asset type facts, respecting User settings built-in availability.
