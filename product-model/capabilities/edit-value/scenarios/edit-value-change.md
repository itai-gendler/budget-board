---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement date or signed amount for the selected valuation snapshot.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::asset-details"
        }
      }
    },
    {
      "text": "The Product changes the selected Value Date and Amount.",
      "kind": "product",
      "entities": [
        {
          "entity": "value",
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
          "place": "web::authenticated::asset-details"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ValueService.cs"
    }
  ]
}
---

# Edit value change

## Trigger

The User submits a replacement date or signed amount for the selected valuation snapshot.

## Outcome

The Product changes the selected Value Date and Amount.
