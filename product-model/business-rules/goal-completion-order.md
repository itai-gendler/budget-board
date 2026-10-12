---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "goal",
      "effect": "changes"
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
      "target": "server/BudgetBoard.Service/GoalService.cs#CompleteEligibleGoalsAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs#SyncAsync"
    }
  ]
}
---

# Goal completion precedes saved Rules during synchronization

Manual completion below 100 allowed; eligible completion before saved Rules; no same-run reevaluation or reopening established.
