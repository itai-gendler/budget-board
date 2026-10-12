---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement limit or rollover start for a selected monthly allocation.",
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
      "text": "The Product changes parent Budget.Limit and Rollover start after checking the child-total floor.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "changes",
          "facts": [
            "Limit",
            "Rollover start"
          ]
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

# Edit budget parent

## Trigger

The User submits a replacement limit or rollover start for a selected monthly allocation.

## Outcome

The Product changes parent Budget.Limit and Rollover start after checking the child-total floor.
