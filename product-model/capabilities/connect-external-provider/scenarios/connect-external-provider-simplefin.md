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
      "text": "The Product exchanges and validates the setup token before retaining SimpleFIN connection.Access credential and refreshes discovered SimpleFIN account metadata with SimpleFIN organization facts. Discovery errors can leave a retained connection after credential validation.",
      "kind": "product",
      "entities": [
        {
          "entity": "simplefin-connection",
          "effect": "creates",
          "facts": [
            "Access credential"
          ]
        },
        {
          "entity": "simplefin-account",
          "effect": "creates",
          "facts": [
            "Provider reference",
            "Name",
            "Currency",
            "Reported balance",
            "Balance date",
            "Sync start",
            "Last sync",
            "Local account link"
          ],
          "with": "simplefin-organization"
        },
        {
          "entity": "simplefin-organization",
          "effect": "creates",
          "facts": [
            "Name",
            "Domain",
            "Provider URL",
            "Institution URL",
            "Provider reference"
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

# Connect external provider SimpleFIN

## Trigger

The User submits a setup token or API credential to establish a provider connection.

## Outcome

The Product exchanges and validates the setup token before retaining SimpleFIN connection.Access credential and refreshes discovered SimpleFIN account metadata with SimpleFIN organization facts. Discovery errors can leave a retained connection after credential validation.

## Edge cases

- A direct provider-handler demo refusal is reported rather than represented as a successful connection.
