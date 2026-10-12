---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a classification, calendar month, limit and optional rollover start.",
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
      "text": "The Product creates valid Budget entries from the batch and reports failed duplicate or invalid entries afterward; already saved allocations remain.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "creates",
          "facts": [
            "Category",
            "Month",
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

# Add budget partial batch

## Trigger

The User submits a classification, calendar month, limit and optional rollover start.

## Outcome

The Product creates valid Budget entries from the batch and reports failed duplicate or invalid entries afterward; already saved allocations remain.
