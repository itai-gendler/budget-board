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
      "id": "account",
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
      "target": "server/BudgetBoard.Service/GoalService.cs#CalculateAverageInterestRate"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#EstimateGoalMonthlyContribution"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#EstimateGoalCompleteDate"
    }
  ]
}
---

# Goal interest estimates retain their signed weighting and arithmetic branches

Signed balance weighting and implemented annuity/logarithmic branches remain distinct. No general arithmetic-validity or financial-accuracy guarantee. Let A be Target, B the latest linked balance total, C Stored contribution, n the calendar-month difference and r the monthly rate. Interest formulas apply when requested and r is positive; otherwise the corresponding noninterest estimate is retained. The monthly rate is sum(rate*balance)/sum(eligible balances)/12, retaining nonzero balances and nonzero weighted terms. Debt dates use ceiling(log((C/r)/(C/r-remaining))/log(1+r)); savings dates use ceiling(log((C+r*A)/(C+r*B))/log(1+r)). Date-driven debt contribution uses remaining*r*(1+r)^n/((1+r)^n-1); savings uses r*(A-B*(1+r)^n)/((1+r)^n-1). The implemented debt tests differ by branch and arithmetic domains are not universally guarded.
