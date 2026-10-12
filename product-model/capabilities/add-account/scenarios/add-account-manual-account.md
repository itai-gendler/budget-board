---
{
  "kind": "primary",
  "routes": {
    "accounts": "Accounts",
    "external-accounts": "External accounts"
  },
  "steps": [
    {
      "text": "The User enters a name, selects the containing organization and submits creation.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "accounts": {
          "place": "web::authenticated::accounts"
        },
        "external-accounts": {
          "place": "web::authenticated::external-accounts"
        }
      }
    },
    {
      "text": "The Product creates Account with Manual source, empty Type, zero Interest rate, visible flags, initial Order and no deletion marker. A deleted Institution used for creation becomes active.",
      "kind": "product",
      "entities": [
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
          "to": "Active"
        },
        {
          "entity": "institution",
          "effect": "changes",
          "facts": [
            "Deletion date"
          ],
          "from": "Deleted",
          "to": "Active"
        }
      ],
      "actor": "user",
      "contexts": {
        "accounts": {
          "place": "web::authenticated::accounts"
        },
        "external-accounts": {
          "place": "web::authenticated::external-accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs"
    }
  ]
}
---

# Add account manual account

## Trigger

The User enters a name, selects the containing organization and submits creation.

## Outcome

The Product creates Account with Manual source, empty Type, zero Interest rate, visible flags, initial Order and no deletion marker. A deleted Institution used for creation becomes active.

## Edge cases

- A structural demo-filter refusal is reported without creating the selected record.
