---
{
  "kind": "primary",
  "routes": {
    "accounts": "Accounts",
    "account-details": "Account details"
  },
  "steps": [
    {
      "text": "The User opens the active collection and selects a record to inspect its dated history.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "accounts": {
          "place": "web::authenticated::accounts"
        },
        "account-details": {
          "place": "web::authenticated::account-details"
        }
      }
    },
    {
      "text": "The Product presents active Account facts grouped by Institution and the latest Balance amount; detail reads dated history.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name",
            "Type",
            "Interest rate",
            "Source",
            "Account hidden",
            "Transactions hidden",
            "Order",
            "Deletion date"
          ]
        },
        {
          "entity": "institution",
          "effect": "reads",
          "facts": [
            "Name",
            "Order",
            "Deletion date"
          ]
        },
        {
          "entity": "balance",
          "effect": "reads",
          "facts": [
            "Date",
            "Amount"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "accounts": {
          "place": "web::authenticated::accounts"
        },
        "account-details": {
          "place": "web::authenticated::account-details"
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

# Browse accounts active collection and detail

## Trigger

The User opens the active collection and selects a record to inspect its dated history.

## Outcome

The Product presents active Account facts grouped by Institution and the latest Balance amount; detail reads dated history.
