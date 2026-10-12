---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to the selected target’s name, amount or schedule.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::goal-details"
        }
      }
    },
    {
      "text": "The Product saves supplied Goal Name, Target, Stored contribution and Stored target date. Goal’s linked membership and Initial amount are not edited by this operation.",
      "kind": "product",
      "entities": [
        {
          "entity": "goal",
          "effect": "changes",
          "facts": [
            "Name",
            "Target",
            "Stored contribution",
            "Stored target date"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::goal-details"
        }
      }
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

# Edit goal change schedule and target

## Trigger

The User submits changes to the selected target’s name, amount or schedule.

## Outcome

The Product saves supplied Goal Name, Target, Stored contribution and Stored target date. Selected accounts and Initial amount are not edited by this operation.
