---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected valuation snapshot.",
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
      "text": "The Product removes the selected Value snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "value",
          "effect": "removes"
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

# Delete value remove

## Trigger

The User confirms removal of the selected valuation snapshot.

## Outcome

The Product removes the selected Value snapshot.
