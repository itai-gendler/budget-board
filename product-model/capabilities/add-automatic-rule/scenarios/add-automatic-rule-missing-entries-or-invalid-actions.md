---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits nonempty condition and action lists to save a rule.",
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
      "text": "Missing conditions/actions or invalid action definitions report refusal without creating a saved rule.",
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

# Add automatic rule missing entries or invalid actions

## Trigger

The User submits nonempty condition and action lists to save a rule.

## Outcome

Missing conditions/actions or invalid action definitions report refusal without creating a saved rule.
