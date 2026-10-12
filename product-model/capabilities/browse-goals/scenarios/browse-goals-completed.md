---
{
  "kind": "primary",
  "routes": {
    "goals": "Goals",
    "goal-details": "Goal details"
  },
  "steps": [
    {
      "text": "The User opens linked savings or debt targets and inspects progress, planning estimates and completion.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "goals": {
          "place": "web::authenticated::goals"
        },
        "goal-details": {
          "place": "web::authenticated::goal-details"
        }
      }
    },
    {
      "text": "The Product presents completed Goal planning facts and Completed date with latest linked Balance results; reopening is not established.",
      "kind": "product",
      "entities": [
        {
          "entity": "goal",
          "effect": "reads",
          "facts": [
            "Name",
            "Target",
            "Initial amount",
            "Selected accounts",
            "Stored contribution",
            "Stored target date",
            "Completed date"
          ]
        },
        {
          "entity": "balance",
          "effect": "reads",
          "facts": [
            "Date",
            "Amount"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "goals": {
          "place": "web::authenticated::goals"
        },
        "goal-details": {
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

# Browse goals completed

## Trigger

The User opens account-linked Goals and inspects progress, planning estimates and completion.

## Outcome

The Product presents completed Goal planning facts and Completed date with latest linked Balance results; reopening is not established.
