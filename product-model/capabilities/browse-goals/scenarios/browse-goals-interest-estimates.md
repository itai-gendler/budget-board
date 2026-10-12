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
      "text": "The Product presents Goal interest estimates using signed Account.Interest rate and Balance weighting and the implemented annuity/logarithmic branches. Arithmetic inputs are not universally guarded and financial accuracy is not promised.",
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

# Browse goals interest estimates

## Trigger

The User opens account-linked Goals and inspects progress, planning estimates and completion.

## Outcome

The Product presents Goal interest estimates using signed Account.Interest rate and Balance weighting and the implemented annuity/logarithmic branches. Arithmetic inputs are not universally guarded and financial accuracy is not promised.
