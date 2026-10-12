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
      ],
      "collects": [
        "Name",
        "Target",
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Goals/GoalCard/EditableGoalCardContent/EditableGoalCardContent.tsx#EditableGoalCardContent"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Goals/GoalDetails/GoalDetails.tsx#GoalDetails"
    }
  ]
}
---

# Goal details

The selected Goal’s planning information, editable name, target and schedule, linked Accounts and dated balance history. Editing occurs in the selected Goal card; the account/history detail view shows linked sources. Monthly progress and interest results are calculated outputs.
