---
{
  "kind": "validation",
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
      "text": "A warning percentage below zero or above one hundred reports refusal without saving the setting.",
      "kind": "condition",
      "entities": [],
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

# Change budget settings out of range

## Trigger

The User submits the warning threshold percentage.

## Outcome

A warning percentage below zero or above one hundred reports refusal without saving the setting.
