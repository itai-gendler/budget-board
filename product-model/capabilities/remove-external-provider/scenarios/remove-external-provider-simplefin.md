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
      "text": "The Product clears SimpleFIN connection and removes discovered SimpleFIN account and SimpleFIN organization records. Linked Account.Source returns to Manual, preserving local financial history. Credential clearing and metadata removal do not establish atomic rollback.",
      "kind": "product",
      "entities": [
        {
          "entity": "simplefin-connection",
          "effect": "removes"
        },
        {
          "entity": "simplefin-account",
          "effect": "removes",
          "with": "simplefin-organization"
        },
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Source"
          ]
        },
        {
          "entity": "simplefin-organization",
          "effect": "removes"
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

# Remove external provider SimpleFIN

## Trigger

The User confirms removal of the selected provider connection.

## Outcome

The Product clears SimpleFIN connection and removes discovered SimpleFIN account and SimpleFIN organization records. Linked Account.Source returns to Manual, preserving local financial history. Credential clearing and metadata removal do not establish atomic rollback.

## Edge cases

- A direct provider-handler demo refusal leaves the connection request unapplied.
