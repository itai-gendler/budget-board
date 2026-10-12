---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an amount for a date already represented by a snapshot.",
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
      "text": "The Product replaces Balance.Amount on the existing Date instead of adding a second snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "balance",
          "effect": "changes",
          "facts": [
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

# Add balance overwrite same date

## Trigger

The User submits an amount for a date already represented by a snapshot.

## Outcome

The Product replaces Balance.Amount on the existing Date instead of adding a second snapshot.
