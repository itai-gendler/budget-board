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
      "target": "server/BudgetBoard.Service/GoalService.cs#EstimateGoalMonthlyContribution"
    }
  ]
}
---

# Date-driven contribution uses its literal remaining-amount branch

Savings `A−(B−I)`; `A==0` debt branch; calendar-month difference; nonpositive month difference returns remaining amount; stored contribution returned directly. A stored contribution is returned directly. Otherwise remaining is A-(B-I), except A==0 uses abs(B). Divide by calendar-month difference n when n>0; n<=0 returns the remaining amount.
