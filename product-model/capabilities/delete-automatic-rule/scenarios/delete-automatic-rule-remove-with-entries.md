---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of a saved rule and its entries.",
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
      "text": "The Product removes Automatic rule and its contained Rule condition and Rule action entries.",
      "kind": "product",
      "entities": [
        {
          "entity": "automatic-rule",
          "effect": "removes"
        },
        {
          "entity": "rule-condition",
          "effect": "removes",
          "with": "automatic-rule"
        },
        {
          "entity": "rule-action",
          "effect": "removes",
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

# Delete automatic rule remove with entries

## Trigger

The User confirms removal of a saved rule and its entries.

## Outcome

The Product removes Automatic rule and its contained Rule condition and Rule action entries.
