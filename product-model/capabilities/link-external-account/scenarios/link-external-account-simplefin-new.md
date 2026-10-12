---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects an existing local record or creates one inline and submits the provider link.",
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
      "text": "The Product links SimpleFIN account to a newly created Account, sets the linked Account.Source to SimpleFIN, resets provider Last sync and returns any previous linked Account.Source to Manual. Record validation does not establish cross-provider exclusivity.",
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
          ],
          "as": "previous-link"
        },
        {
          "entity": "account",
          "effect": "creates",
          "facts": [
            "Name",
            "Type",
            "Interest rate",
            "Source",
            "Account hidden",
            "Transactions hidden",
            "Order",
            "Deletion date"
          ],
          "as": "new-link",
          "to": "Active"
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

# Link external account SimpleFIN new

## Trigger

The User selects an existing local record or creates one inline and submits the provider link.

## Outcome

The Product links SimpleFIN account to a newly created Account, sets the linked Account.Source to SimpleFIN, resets provider Last sync and returns any previous linked Account.Source to Manual. Record validation does not establish cross-provider exclusivity.
