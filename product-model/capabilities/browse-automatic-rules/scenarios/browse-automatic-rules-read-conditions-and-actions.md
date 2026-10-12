---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens saved rules and their condition/action entries.",
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
      "text": "The Product presents Automatic rule collections with ordered Rule condition and Rule action fields and input.",
      "kind": "product",
      "entities": [
        {
          "entity": "automatic-rule",
          "effect": "reads",
          "facts": [
            "Conditions",
            "Actions"
          ]
        },
        {
          "entity": "rule-condition",
          "effect": "reads",
          "facts": [
            "Field",
            "Operator",
            "Comparison value"
          ]
        },
        {
          "entity": "rule-action",
          "effect": "reads",
          "facts": [
            "Field",
            "Operator",
            "Action value"
          ]
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

# Browse automatic rules read conditions and actions

## Trigger

The User opens saved rules and their condition/action entries.

## Outcome

The Product presents Automatic rule collections with ordered Rule condition and Rule action fields and values.
