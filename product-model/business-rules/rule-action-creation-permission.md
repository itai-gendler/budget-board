---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "rule-action",
      "effect": "creates",
      "contexts": [
        {
          "place": "web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "automatic-rule"
        },
        {
          "verb": "owns",
          "entity": "user"
        }
      ]
    }
  ]
}
---

# Only the owning User creates Rule action

The owning User may create Rule action through the declared ownership path in the authenticated Experience.
