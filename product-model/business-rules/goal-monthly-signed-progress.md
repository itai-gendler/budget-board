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
      "id": "transaction",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#GetGoalMonthlyContributionProgress"
    }
  ]
}
---

# Goal monthly progress includes signed linked-account transactions

All linked-account signed Transactions in server current month; no Budget exclusions or today cutoff.
