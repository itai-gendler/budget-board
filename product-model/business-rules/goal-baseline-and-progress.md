---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "goal",
      "effect": "creates"
    },
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
      "target": "server/BudgetBoard.Service/GoalService.cs#CreateGoalAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#CalculatePercentComplete"
    }
  ]
}
---

# Goal progress uses its retained baseline and latest linked balances

Baseline choice, latest balances, negative-baseline target, upper-only cap and zero-target result. Let A be Target, B the latest linked-account balance total and I Initial amount. Creation chooses I=0 when existing balances apply, otherwise I=B. Progress is (B-I)/D*100, with D=abs(I) for I<0 and D=A otherwise. D=0 returns zero; only the upper bound is capped at 100. Multiple Goals may use the same Account.
