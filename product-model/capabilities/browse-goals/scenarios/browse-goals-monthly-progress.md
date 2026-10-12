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
      "text": "The Product presents Goal monthly contribution progress as the signed sum of Transaction amounts on Goal’s linked membership in the server’s current calendar month. This computation applies no deletion, visibility, transfer or today cutoff.",
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
          "entity": "transaction",
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

# Browse goals monthly progress

## Trigger

The User opens account-linked Goals and inspects progress, planning estimates and completion.

## Outcome

The Product presents Goal monthly contribution progress as the signed sum of Transaction amounts on Goal’s linked membership in the server’s current calendar month. This computation applies no deletion, visibility, transfer or today cutoff.
