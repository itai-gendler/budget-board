---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User adds a comparison field, operator and comparison input to the saved condition list.",
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
      "text": "The submitted nonempty condition list adds an entry. The Product replaces Rule condition instances and changes Automatic rule.Conditions; stable entry identity is not preserved.",
      "kind": "product",
      "entities": [
        {
          "entity": "automatic-rule",
          "effect": "changes",
          "facts": [
            "Conditions"
          ]
        },
        {
          "entity": "rule-condition",
          "effect": "removes",
          "as": "previous-entries"
        },
        {
          "entity": "rule-condition",
          "effect": "creates",
          "facts": [
            "Field",
            "Operator",
            "Comparison value"
          ],
          "as": "replacement-entries"
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

# Add rule condition add entry

## Trigger

The User adds a comparison field, operator and comparison input to the saved condition list.

## Outcome

The submitted nonempty condition list adds an entry. The Product replaces Rule condition instances and changes Automatic rule.Conditions; stable entry identity is not preserved.
