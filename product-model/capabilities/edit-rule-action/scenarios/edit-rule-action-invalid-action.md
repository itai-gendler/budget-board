---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the selected action field, operator or action input and saves the list.",
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

# Edit rule action invalid action

## Trigger

The User changes the selected action field, operator or action input and saves the list.

## Outcome

Invalid action field, operator, category, tag input or amount expression reports refusal before saving the replacement list.
