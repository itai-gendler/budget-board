---
{
  "kind": "primary",
  "routes": {
    "goals": "Goals",
    "goal-details": "Goal details"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected financial target.",
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
      "text": "The Product removes Goal while retaining its linked financial records.",
      "kind": "product",
      "entities": [
        {
          "entity": "goal",
          "effect": "removes",
          "from": "Active"
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

# Delete goal remove

## Trigger

The User confirms removal of the selected financial target.

## Outcome

The Product removes Goal while retaining its linked financial records.

## Edge cases

- The deletion handler accepts completed records too; completed summaries do not expose that action. Any accepted removal preserves linked financial records.
