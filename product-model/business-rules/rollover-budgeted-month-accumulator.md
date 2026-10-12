---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "budget",
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
      "target": "server/BudgetBoard.Service/BudgetService.cs#CalculateRollover"
    }
  ]
}
---

# Rollover accumulates prior budgeted-month remainders including deficits

Signed prior budgeted-month remainders, deficits and skipped unbudgeted months; nonrolling parent may sum child rollover. For each prior month retaining that category’s Budget, add Limit minus signed spending. Skip unbudgeted months and their spending; keep negative remainders. Clamp the start to the effective earlier range. A parent without its own rollover can sum children’s rollover.
