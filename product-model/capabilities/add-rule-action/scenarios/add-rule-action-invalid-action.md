---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User adds an action field, operator and action input to the saved action list.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::automatic-rules"
        }
      }
    },
    {
      "text": "Invalid action field, operator, classification, label input or amount expression reports refusal before saving the replacement list.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::automatic-rules"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    }
  ]
}
---

# Add rule action invalid action

## Trigger

The User adds an action field, operator and action input to the saved action list.

## Outcome

Invalid action field, operator, category, tag input or amount expression reports refusal before saving the replacement list.
