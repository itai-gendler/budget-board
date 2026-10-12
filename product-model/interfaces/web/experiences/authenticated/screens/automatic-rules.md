---
{
  "entities": [
    {
      "entity": "automatic-rule",
      "shows": [
        "Conditions",
        "Actions"
      ]
    },
    {
      "entity": "rule-condition",
      "shows": [
        "Field",
        "Operator",
        "Comparison value"
      ],
      "collects": [
        "Field",
        "Operator",
        "Comparison value"
      ]
    },
    {
      "entity": "rule-action",
      "shows": [
        "Field",
        "Operator",
        "Action value"
      ],
      "collects": [
        "Field",
        "Operator",
        "Action value"
      ]
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

# Automatic rules

Rules and condition/action entry editing. Shows and collects Field, Operator, Comparison value and Action value.
