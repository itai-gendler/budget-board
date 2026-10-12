---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User removes the selected comparison entry and saves the remaining list.",
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
      "text": "The submitted nonempty condition list omits the selected entry. The Product replaces Rule condition instances and changes Automatic rule.Conditions; stable entry identity is not preserved.",
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

# Remove rule condition remove entry

## Trigger

The User removes the selected comparison entry and saves the remaining list.

## Outcome

The submitted nonempty condition list omits the selected entry. The Product replaces Rule condition instances and changes Automatic rule.Conditions; stable entry identity is not preserved.
