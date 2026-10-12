---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects a month already containing allocations and attempts Copy Previous.",
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
      "text": "The browser Copy Previous action is unavailable for a nonempty selected month; this outcome does not establish a server overwrite guarantee.",
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

# Copy previous budgets target not empty

## Trigger

The User selects a month already containing allocations and attempts Copy Previous.

## Outcome

The browser Copy Previous action is unavailable for a nonempty selected month; this outcome does not establish a server overwrite guarantee.
