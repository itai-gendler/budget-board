---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a date and signed amount for a dated snapshot.",
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
      "text": "The Product creates a dated Balance snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "balance",
          "effect": "creates",
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

# Add balance add

## Trigger

The User submits a date and signed amount for a dated snapshot.

## Outcome

The Product creates a dated Balance snapshot.
