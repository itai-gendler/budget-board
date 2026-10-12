---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the new ordering of the selected collection.",
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
      "text": "The Product saves Account.Order for the supplied collection ordering.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Order"
          ]
        }
      ],
      "actor": "user",
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
    }
  ]
}
---

# Order accounts save order

## Trigger

The User submits the new ordering of the selected collection.

## Outcome

The Product saves Account.Order for the supplied collection ordering.

## Edge cases

- A structural demo-filter refusal preserves the existing ordering.
