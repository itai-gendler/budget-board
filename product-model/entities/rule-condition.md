---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    }
  ],
  "domain": "automatic-rules"
}
---

# Rule condition

Added, replaced and removed within a Rule. Stable identity across replacement is not promised.

## Information kept

- **Field** — Transaction fact selected by this entry.
- **Operator** — Matching or action operator.
- **Comparison value** — Input compared while evaluating a condition.
