---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected dated snapshot.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-details"
        }
      }
    },
    {
      "text": "The Product removes the selected Balance snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "balance",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-details"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BalanceService.cs"
    }
  ]
}
---

# Delete balance remove

## Trigger

The User confirms removal of the selected dated snapshot.

## Outcome

The Product removes the selected Balance snapshot.
