---
{
  "entities": [
    {
      "entity": "goal",
      "collects": [
        "Name",
        "Target",
        "Selected accounts",
        "Stored contribution",
        "Stored target date"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name"
      ]
    },
    {
      "entity": "balance",
      "shows": [
        "Date",
        "Amount"
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

# Add Goal

Goal creation process; all wizard stages remain here. Collects Name, Target, selected Accounts and one schedule input. Applying existing balances is a creation choice.
