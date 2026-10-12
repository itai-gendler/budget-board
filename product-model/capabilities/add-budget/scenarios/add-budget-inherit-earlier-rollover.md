---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a new month for a classification with an earlier rollover setting.",
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
      "text": "The Product creates Budget with the most recent earlier classification Rollover start. A parent/child conflict drops the created rollover rather than accepting both.",
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

# Add budget inherit earlier rollover

## Trigger

The User submits a new month for a classification with an earlier rollover setting.

## Outcome

The Product creates Budget with the most recent earlier category Rollover start. A parent/child conflict drops the created rollover rather than accepting both.
