---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the warning threshold percentage.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budget-settings"
        }
      }
    },
    {
      "text": "The Product saves the warning percentage in User settings between zero and one hundred; warning behavior uses that selected percentage.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Budget warning threshold"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budget-settings"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    }
  ]
}
---

# Change budget settings set warning threshold

## Trigger

The User submits the warning threshold percentage.

## Outcome

The Product saves User settings.Budget warning threshold between zero and one hundred; warning behavior uses that selected percentage.
