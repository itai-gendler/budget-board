---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the selected comparison field, operator or comparison input and saves the list.",
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
      "text": "The submitted nonempty condition list changes the selected entry. The Product replaces Rule condition instances and changes Automatic rule.Conditions; stable entry identity is not preserved.",
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

# Edit rule condition replace entry

## Trigger

The User changes the selected comparison field, operator or comparison input and saves the list.

## Outcome

The submitted nonempty condition list changes the selected entry. The Product replaces Rule condition instances and changes Automatic rule.Conditions; stable entry identity is not preserved.
