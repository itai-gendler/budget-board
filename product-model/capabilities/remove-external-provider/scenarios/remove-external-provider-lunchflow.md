---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected provider connection.",
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
      "text": "The Product clears LunchFlow connection and removes discovered LunchFlow account records. Linked Account.Source returns to Manual, preserving local financial history. Credential clearing and metadata removal do not establish atomic rollback.",
      "kind": "product",
      "entities": [
        {
          "entity": "lunchflow-connection",
          "effect": "removes"
        },
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

# Remove external provider LunchFlow

## Trigger

The User confirms removal of the selected provider connection.

## Outcome

The Product clears LunchFlow connection and removes discovered LunchFlow account records. Linked Account.Source returns to Manual, preserving local financial history. Credential clearing and metadata removal do not establish atomic rollback.
