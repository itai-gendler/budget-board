---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of a selected monthly allocation.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budgets"
        }
      }
    },
    {
      "text": "The Product removes parent Budget and same-month child Budget records.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "removes",
          "as": "parent"
        },
        {
          "entity": "budget",
          "effect": "removes",
          "as": "children"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::budgets"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    }
  ]
}
---

# Delete budget parent with children

## Trigger

The User confirms removal of a selected monthly allocation.

## Outcome

The Product removes parent Budget and same-month child Budget records.
