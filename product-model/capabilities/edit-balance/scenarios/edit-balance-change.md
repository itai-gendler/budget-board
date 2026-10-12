---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement date or signed amount for the selected snapshot.",
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
      "text": "The Product changes the selected Balance Date and Amount.",
      "kind": "product",
      "entities": [
        {
          "entity": "balance",
          "effect": "changes",
          "facts": [
            "Date",
            "Amount"
          ]
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

# Edit balance change

## Trigger

The User submits a replacement date or signed amount for the selected snapshot.

## Outcome

The Product changes the selected Balance Date and Amount.
