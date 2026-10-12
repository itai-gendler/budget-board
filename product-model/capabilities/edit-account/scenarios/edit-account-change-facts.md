---
{
  "kind": "primary",
  "routes": {
    "accounts": "Accounts",
    "account-details": "Account details"
  },
  "steps": [
    {
      "text": "The User submits the selected record’s name, type or interest rate.",
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
      "text": "The Product saves supplied Account Name, Type and Interest rate. Empty name input leaves the existing name.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Name",
            "Type",
            "Interest rate"
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

# Edit account change facts

## Trigger

The User submits the selected record’s name, type or interest rate.

## Outcome

The Product saves supplied Account Name, Type and Interest rate. Empty name input leaves the existing name.
