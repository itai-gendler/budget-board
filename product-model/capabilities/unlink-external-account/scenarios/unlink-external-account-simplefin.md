---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Unlink for the selected provider record.",
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
      "text": "The Product clears SimpleFIN account.Local account link and Last sync and returns the former linked Account.Source to Manual.",
      "kind": "product",
      "entities": [
        {
          "entity": "simplefin-account",
          "effect": "changes",
          "facts": [
            "Local account link",
            "Last sync"
          ]
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

# Unlink external account SimpleFIN

## Trigger

The User chooses Unlink for the selected provider record.

## Outcome

The Product clears SimpleFIN account.Local account link and Last sync and returns the former linked Account.Source to Manual.

## Edge cases

- A direct provider-handler demo refusal leaves the requested unlink unapplied.
