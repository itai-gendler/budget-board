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
      "text": "The Product presents Goal progress from latest linked Balance total B and baseline I, using target A when I is nonnegative. Progress is (B-I)/A*100 with an upper cap and zero-target result. Date-driven remaining is A-(B-I); contribution-driven date remaining is A-I-B.",
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

# Browse goals savings

## Trigger

The User opens account-linked Goals and inspects progress, planning estimates and completion.

## Outcome

The Product presents Goal progress from latest linked Balance total B and baseline I, using target A when I is nonnegative. Progress is (B-I)/A*100 with an upper cap and zero-target result. Date-driven remaining is A-(B-I); contribution-driven date remaining is A-I-B.
