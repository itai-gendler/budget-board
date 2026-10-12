---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens discovered provider records and their local links.",
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
      "text": "The Product presents LunchFlow account discovery, reported currency/snapshot amount, Sync start, Last sync and Local account link, alongside matching Account names. Stored provider credentials are not disclosed.",
      "kind": "product",
      "entities": [
        {
          "entity": "lunchflow-account",
          "effect": "reads",
          "facts": [
            "Provider reference",
            "Name",
            "Institution name",
            "Provider",
            "Status",
            "Currency",
            "Reported balance",
            "Balance date",
            "Sync start",
            "Last sync",
            "Local account link"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name",
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

# Browse external accounts LunchFlow

## Trigger

The User opens discovered provider records and their local links.

## Outcome

The Product presents LunchFlow account discovery, reported currency/balance, Sync start, Last sync and Local account link, alongside matching Account names. Stored provider credentials are not disclosed.
