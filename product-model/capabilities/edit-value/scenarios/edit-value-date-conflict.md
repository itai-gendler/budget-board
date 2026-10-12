---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement date belonging to another retained valuation snapshot.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::asset-details"
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
          "place": "web::authenticated::asset-details"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ValueService.cs"
    }
  ]
}
---

# Edit value date conflict

## Trigger

The User submits a replacement date belonging to another retained valuation snapshot.

## Outcome

Moving a snapshot into another existing date reports a conflict without overwriting that other record.
