---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a new history start date for the selected provider record.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::external-accounts"
        }
      }
    },
    {
      "text": "The Product saves SimpleFIN account.Sync start, which limits provider-history retrieval for this discovered record.",
      "kind": "product",
      "entities": [
        {
          "entity": "simplefin-account",
          "effect": "changes",
          "facts": [
            "Sync start"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::external-accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    }
  ]
}
---

# Change sync start date SimpleFIN

## Trigger

The User submits a new history start date for the selected provider record.

## Outcome

The Product saves SimpleFIN account.Sync start, which limits provider-history retrieval for this discovered record.

## Edge cases

- A direct provider-handler demo refusal preserves the selected history start.
