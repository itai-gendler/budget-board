---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    }
  ],
  "relations": [
    {
      "entity": "rule-condition",
      "verb": "contains",
      "cardinality": "one-to-many"
    },
    {
      "entity": "rule-action",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "automatic-rules"
}
---

# Automatic rule

Created, changed through entry replacement, run and removed.

## Information kept

- **Conditions** — Contained matching entries, evaluated with AND.
- **Actions** — Contained action entries, evaluated in order.
