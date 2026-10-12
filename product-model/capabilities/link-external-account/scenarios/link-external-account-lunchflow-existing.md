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
      "text": "The Product links LunchFlow account to the selected existing Account, sets the linked Account.Source to LunchFlow, resets provider Last sync and returns any previous linked Account.Source to Manual. Record validation does not establish cross-provider exclusivity.",
      "kind": "product",
      "entities": [
        {
          "entity": "lunchflow-account",
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
          "effect": "changes",
          "facts": [
            "Source"
          ],
          "as": "new-link"
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

# Link external account LunchFlow existing

## Trigger

The User selects an existing local record or creates one inline and submits the provider link.

## Outcome

The Product links LunchFlow account to the selected existing Account, sets the linked Account.Source to LunchFlow, resets provider Last sync and returns any previous linked Account.Source to Manual. Record validation does not establish cross-provider exclusivity.
