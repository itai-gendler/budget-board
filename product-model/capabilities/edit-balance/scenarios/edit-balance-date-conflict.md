---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement date belonging to another retained snapshot.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-details"
        }
      }
    },
    {
      "text": "Moving a snapshot into another existing date reports a conflict without overwriting that other record.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-details"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BalanceService.cs"
    }
  ]
}
---

# Edit balance date conflict

## Trigger

The User submits a replacement date belonging to another retained snapshot.

## Outcome

Moving a snapshot into another existing date reports a conflict without overwriting that other record.
