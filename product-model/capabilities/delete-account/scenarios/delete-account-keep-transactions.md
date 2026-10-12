---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms deletion and chooses to keep the financial activity history.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    },
    {
      "text": "The Product marks the selected Account Deleted and clears Type, retaining its original Source until history deletion has been processed.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Type",
            "Deletion date"
          ],
          "from": "Active",
          "to": "Deleted"
        }
      ],
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    },
    {
      "text": "The Product retains financial activity history. If this was the last active Account, Institution becomes Deleted and its Order resets to zero. Linked SimpleFIN account and LunchFlow account metadata is detached and its Last sync cleared.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "institution",
          "effect": "changes",
          "facts": [
            "Deletion date",
            "Order"
          ],
          "from": "Active",
          "to": "Deleted"
        },
        {
          "entity": "simplefin-account",
          "effect": "changes",
          "facts": [
            "Local account link",
            "Last sync"
          ]
        },
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
          "effect": "reads",
          "facts": [
            "Deletion date"
          ]
        }
      ],
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    },
    {
      "text": "After the optional history effects, the Product sets Account.Source to Manual.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Source"
          ]
        }
      ],
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/InstitutionService.cs#DeleteInstitutionAsync"
    }
  ]
}
---

# Delete account keep transactions

## Trigger

The User confirms deletion and chooses to keep the financial activity history.

## Outcome

The Product marks Account deleted, clears its Type, returns Source to Manual and detaches linked SimpleFIN account or LunchFlow account. The Institution is marked deleted and its Order resets to zero only when it has no active accounts. Retained transaction history is not deleted by this choice.

## Edge cases

- A structural demo-filter refusal is reported without applying the requested deletion.
