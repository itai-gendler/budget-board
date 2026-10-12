---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "Synchronization has refreshed dated monetary snapshots and reached automatic target completion.",
      "kind": "condition",
      "entities": [],
      "unattended": true,
      "contexts": {
        "web": {
          "place": "web::authenticated"
        }
      }
    },
    {
      "text": "Synchronization reads Goal and latest Account Balance results, marks eligible Goal records Completed and records Completed date before saved-rule execution. Later rule changes do not trigger same-run completion reevaluation.",
      "kind": "product",
      "entities": [
        {
          "entity": "goal",
          "effect": "changes",
          "facts": [
            "Completed date"
          ],
          "from": "Active",
          "to": "Completed"
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
      "contexts": {
        "web": {
          "place": "web::authenticated"
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

# Complete goal unattended sync completion

## Trigger

Synchronization has refreshed dated monetary snapshots and reached automatic target completion.

## Outcome

Synchronization reads Goal and latest Account Balance results, marks eligible Goal records Completed and records Completed date before saved-rule execution. Later rule changes do not trigger same-run completion reevaluation.
