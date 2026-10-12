---
{
  "kind": "validation",
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
      "text": "A probability percentage outside zero through one hundred reports refusal without saving that setting.",
      "kind": "condition",
      "entities": [],
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

# Change auto categorizer settings invalid threshold

## Trigger

The User submits the enabled setting and minimum accepted probability percentage.

## Outcome

A probability percentage outside zero through one hundred reports refusal without saving that setting.
