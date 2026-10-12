---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the enabled setting and minimum accepted probability percentage.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::auto-categorizer"
        }
      }
    },
    {
      "text": "With a retained trained classifier, the Product saves the activation selection in User settings and Minimum probability percentage. Activation without a model is refused.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Auto categorizer enabled",
            "Minimum probability percentage"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::auto-categorizer"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    }
  ]
}
---

# Change auto categorizer settings enable and set threshold

## Trigger

The User submits the enabled setting and minimum accepted probability percentage.

## Outcome

With a retained trained classifier, the Product saves User settings.Auto categorizer enabled and Minimum probability percentage. Activation without a model is refused.
