---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a setup token or API credential to establish a provider connection.",
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
      "text": "The Product validates a nonempty API key before retaining LunchFlow connection.API credential and refreshes discovered LunchFlow account metadata. Discovery errors can leave a retained connection after credential validation.",
      "kind": "product",
      "entities": [
        {
          "entity": "lunchflow-connection",
          "effect": "creates",
          "facts": [
            "API credential"
          ]
        },
        {
          "entity": "lunchflow-account",
          "effect": "creates",
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

# Connect external provider LunchFlow

## Trigger

The User submits a setup token or API credential to establish a provider connection.

## Outcome

The Product validates a nonempty API key before retaining LunchFlow connection.API credential and refreshes discovered LunchFlow account metadata. Discovery errors can leave a retained connection after credential validation.
