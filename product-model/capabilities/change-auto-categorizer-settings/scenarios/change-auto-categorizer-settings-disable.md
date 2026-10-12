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
      "text": "The Product clears the activation selection in User settings while retaining the trained model and threshold.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Auto categorizer enabled"
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

# Change auto categorizer settings disable

## Trigger

The User submits the enabled setting and minimum accepted probability percentage.

## Outcome

The Product clears User settings.Auto categorizer enabled while retaining the trained model and threshold.
