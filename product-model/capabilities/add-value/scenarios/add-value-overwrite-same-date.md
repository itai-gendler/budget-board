---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a valuation amount for an already represented date.",
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
      "text": "The Product replaces Value.Amount on the existing Date instead of adding a second snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "value",
          "effect": "changes",
          "facts": [
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

# Add value overwrite same date

## Trigger

The User submits a valuation amount for an already represented date.

## Outcome

The Product replaces Value.Amount on the existing Date instead of adding a second snapshot.
