---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms deletion together with the financial activity history.",
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
      "text": "The Product soft-deletes the selected Transaction history, clears classification, Tags and Transfer counterpart, detaches retained Transaction counterparts and removes orphan Tag records. Original Manual Account.Source subtracts amounts from Balance snapshots. If this was the last active Account, Institution becomes Deleted and its Order resets to zero; linked SimpleFIN account and LunchFlow account metadata is detached.",
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
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Deletion date",
            "Category",
            "Subcategory",
            "Tags",
            "Transfer counterpart"
          ],
          "from": "Active",
          "to": "Deleted",
          "as": "selected-history"
        },
        {
          "entity": "balance",
          "effect": "changes",
          "facts": [
            "Amount"
          ]
        },
        {
          "entity": "tag",
          "effect": "removes"
        },
        {
          "entity": "transaction",
          "as": "retained-counterparts",
          "effect": "changes",
          "facts": [
            "Transfer counterpart"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
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

# Delete account delete transactions

## Trigger

The User confirms deletion together with the financial activity history.

## Outcome

The Product marks Account deleted, clears its Type, returns Source to Manual and detaches linked SimpleFIN account or LunchFlow account. The Institution is marked deleted and its Order resets to zero only when it has no active accounts. Selected Transaction history is also soft-deleted with its manual Balance adjustments and orphan Tag cleanup.

## Edge cases

- Last-active-account deletion can also directly mark still-active history on previously deleted sibling records through the Institution service, without ordinary ledger adjustment, tag clearing or link removal.
