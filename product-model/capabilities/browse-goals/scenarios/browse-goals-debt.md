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
      "text": "The Product presents Goal progress using abs(Initial amount) when that baseline is negative. Latest Balance totals are signed. Contribution estimation uses Target==0 as its debt test, while date remaining uses negative Initial amount; both retain their implemented formulas.",
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
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Interest rate"
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

# Browse goals debt

## Trigger

The User opens account-linked Goals and inspects progress, planning estimates and completion.

## Outcome

The Product presents Goal progress using abs(Initial amount) when that baseline is negative. Latest Balance totals are signed. Contribution estimation uses Target==0 as its debt test, while date remaining uses negative Initial amount; both retain their implemented formulas.
