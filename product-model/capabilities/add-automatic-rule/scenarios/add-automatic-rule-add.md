---
{
  "kind": "primary",
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
      "text": "The Product creates Automatic rule with nonempty Conditions and Actions, containing Rule condition and Rule action entries. Actions are validated at creation; condition errors may remain until execution.",
      "kind": "product",
      "entities": [
        {
          "entity": "automatic-rule",
          "effect": "creates",
          "facts": [
            "Conditions",
            "Actions"
          ]
        },
        {
          "entity": "rule-condition",
          "effect": "creates",
          "facts": [
            "Field",
            "Operator",
            "Comparison value"
          ],
          "with": "automatic-rule"
        },
        {
          "entity": "rule-action",
          "effect": "creates",
          "facts": [
            "Field",
            "Operator",
            "Action value"
          ],
          "with": "automatic-rule"
        }
      ],
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

# Add automatic rule add

## Trigger

The User submits nonempty condition and action lists to save a rule.

## Outcome

The Product creates Automatic rule with nonempty Conditions and Actions, containing Rule condition and Rule action entries. Actions are validated at creation; condition errors may remain until execution.
