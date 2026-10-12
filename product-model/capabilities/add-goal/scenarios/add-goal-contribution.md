---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a nonzero monthly contribution, target and linked-record selection, with no target date.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::add-goal"
        }
      }
    },
    {
      "text": "The Product creates Goal with the supplied nonzero monthly contribution and selected Account membership. Initial amount is zero when applying existing Balance amounts, otherwise their latest signed total; Completed date is absent. No money is reserved.",
      "kind": "product",
      "entities": [
        {
          "entity": "goal",
          "effect": "creates",
          "facts": [
            "Name",
            "Target",
            "Initial amount",
            "Selected accounts",
            "Stored contribution",
            "Stored target date",
            "Completed date"
          ],
          "to": "Active"
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name"
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
        "web": {
          "place": "web::authenticated::add-goal"
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

# Add goal contribution

## Trigger

The User submits a nonzero monthly contribution, target and linked-record selection, with no target date.

## Outcome

The Product creates Goal with the supplied nonzero monthly contribution and selected Account membership. Initial amount is zero when applying existing Balance amounts, otherwise their latest signed total; Completed date is absent. No money is reserved.
