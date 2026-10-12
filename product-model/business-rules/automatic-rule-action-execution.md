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
      "id": "rule-action",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "tag",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "tag",
      "effect": "removes"
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

# Automatic Rule actions execute sequentially and retain earlier effects on failure

Eligible nondeleted, non-hidden Transactions; sequential actions and caught failures; update count can count one Transaction repeatedly. Amount arithmetic supports `amount`, signs/parentheses with length 256/token 128 limits and distinguished errors. Actions include deletion, Merchant, Category, Notes, Amount, Date and Tag addition/removal. Caught action failures do not roll back earlier actions. Amount expressions accept decimal literals, amount, unary signs, parentheses and + - * /; length is limited to 256 and tokens to 128. Constant zero division, runtime zero division, parsing and overflow retain distinguished errors.
