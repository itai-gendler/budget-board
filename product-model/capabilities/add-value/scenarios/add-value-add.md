---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a date and signed amount for a dated valuation snapshot.",
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
      "text": "The Product creates a dated Value snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "value",
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

# Add value add

## Trigger

The User submits a date and signed amount for a dated valuation snapshot.

## Outcome

The Product creates a dated Value snapshot.
