---
{
  "entities": [
    {
      "entity": "goal",
      "shows": [
        "Name",
        "Target",
        "Initial amount",
        "Selected accounts",
        "Stored contribution",
        "Stored target date",
        "Completed date"
      ]
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

# Goals

Active and completed Goal summaries show planning information, completion and calculated progress. Individual selected targets expose editing and linked-record analysis; monthly progress and interest estimates are derived rather than retained source transactions.
