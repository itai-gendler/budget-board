---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User removes the selected action entry and saves the remaining list.",
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
      "text": "The submitted nonempty action list omits the selected entry. The Product replaces Rule action instances and changes Automatic rule.Actions; stable entry identity is not preserved.",
      "kind": "product",
      "entities": [
        {
          "entity": "automatic-rule",
          "effect": "changes",
          "facts": [
            "Actions"
          ]
        },
        {
          "entity": "rule-action",
          "effect": "removes",
          "as": "previous-entries"
        },
        {
          "entity": "rule-action",
          "effect": "creates",
          "facts": [
            "Field",
            "Operator",
            "Action value"
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

# Remove rule action remove entry

## Trigger

The User removes the selected action entry and saves the remaining list.

## Outcome

The submitted nonempty action list omits the selected entry. The Product replaces Rule action instances and changes Automatic rule.Actions; stable entry identity is not preserved.
