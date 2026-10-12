---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "goal",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#EstimateGoalCompleteDate"
    }
  ]
}
---

# Contribution-driven dates use their distinct remaining-amount branch

Savings `A−I−B`; `I<0` debt branch; ceiling months from current month’s first day; stored date returned directly; missing/zero contribution returns Unix epoch. A stored date is returned directly. Otherwise savings remaining is A-I-B; I<0 uses abs(B). Ceiling(remaining/stored contribution) months are added to the current month’s first day. Missing or zero contribution returns Unix epoch.
