---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the selected record’s Hide setting.",
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
      "text": "The Product sets Asset.Hidden to true.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "changes",
          "facts": [
            "Hidden"
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

# Change asset visibility hide

## Trigger

The User changes the selected record’s Hide setting.

## Outcome

The Product sets Asset.Hidden to true.
