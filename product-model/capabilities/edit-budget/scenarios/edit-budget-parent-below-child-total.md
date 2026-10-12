---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a parent limit below the same-month child total.",
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
      "text": "A parent allocation below the total child limits reports refusal and preserves the existing allocation.",
      "kind": "condition",
      "entities": [],
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

# Edit budget parent below child total

## Trigger

The User submits a parent limit below the same-month child total.

## Outcome

A parent allocation below the total child limits reports refusal and preserves the existing allocation.
