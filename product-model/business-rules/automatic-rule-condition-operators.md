---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "automatic-rule",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "rule-condition",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/AutomaticRuleActionHandler.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/AutomaticRuleConditionHandler.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/AmountExpressionParser.cs"
    }
  ]
}
---

# Automatic Rule conditions combine the shipped operators with AND

AND conditions; shipped string, membership, numeric and date operators; parsing/operator errors remain outcomes. Merchant supports equality/inequality, contains/not-contains, starts/ends and regular expression. Ordinary string matching is culture-insensitive to case; regular expressions retain their own case behavior. Category compares blank, parent or leaf names. Amount uses parsed decimals and equality/inequality/greater/less; Date uses parsed calendar dates and on/before/after; Account uses comma-separated identifiers with membership/nonmembership. Invalid operators and malformed values fail evaluation.
