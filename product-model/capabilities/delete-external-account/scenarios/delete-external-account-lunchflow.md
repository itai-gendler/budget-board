---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected discovered provider record.",
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
      "text": "The Product removes LunchFlow account metadata and returns its linked Account.Source to Manual while retaining local snapshots and financial history.",
      "kind": "product",
      "entities": [
        {
          "entity": "lunchflow-account",
          "effect": "removes"
        },
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Source"
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

# Delete external account LunchFlow

## Trigger

The User confirms removal of the selected discovered provider record.

## Outcome

The Product removes LunchFlow account metadata and returns its linked Account.Source to Manual while retaining local snapshots and transaction history.
