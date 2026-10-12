---
{
  "kind": "primary",
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
      "text": "The submitted nonempty action list adds an entry. The Product replaces Rule action instances and changes Automatic rule.Actions; stable entry identity is not preserved.",
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

# Add rule action add entry

## Trigger

The User adds an action field, operator and action input to the saved action list.

## Outcome

The submitted nonempty action list adds an entry. The Product replaces Rule action instances and changes Automatic rule.Actions; stable entry identity is not preserved.
