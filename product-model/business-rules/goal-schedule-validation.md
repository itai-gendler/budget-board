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
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs"
    }
  ]
}
---

# Goal schedule validation differs between creation and partial edits

Creation date-or-nonzero-contribution and owned Accounts; negative creation contribution not universally refused. Explicit contribution edits reject nonpositive input; partial updates retain their narrower checks.
