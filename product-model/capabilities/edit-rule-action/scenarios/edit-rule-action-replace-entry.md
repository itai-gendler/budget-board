---
{
  "kind": "primary",
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
      "text": "The submitted nonempty action list changes the selected entry. The Product replaces Rule action instances and changes Automatic rule.Actions; stable entry identity is not preserved.",
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

# Edit rule action replace entry

## Trigger

The User changes the selected action field, operator or action input and saves the list.

## Outcome

The submitted nonempty action list changes the selected entry. The Product replaces Rule action instances and changes Automatic rule.Actions; stable entry identity is not preserved.
