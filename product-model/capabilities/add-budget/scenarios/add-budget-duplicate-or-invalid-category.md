---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a duplicate classification/calendar-month pair or invalid classification.",
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
      "text": "A duplicate classification/calendar-month pair or invalid effective classification reports refusal for that entry without overwriting it.",
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

# Add budget duplicate or invalid category

## Trigger

The User submits a duplicate classification/calendar-month pair or invalid classification.

## Outcome

A duplicate category/calendar-month pair or invalid effective category reports refusal for that entry without overwriting it.
