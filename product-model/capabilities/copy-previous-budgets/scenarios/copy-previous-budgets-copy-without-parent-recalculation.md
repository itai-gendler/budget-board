---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Copy Previous for one selected calendar month.",
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
      "text": "For one empty selected month, the Product copies preceding Budget allocations and rollover settings into the target month while suppressing ordinary parent auto-management.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "reads",
          "facts": [
            "Category",
            "Month",
            "Limit",
            "Rollover start"
          ],
          "as": "previous"
        },
        {
          "entity": "budget",
          "effect": "creates",
          "facts": [
            "Category",
            "Month",
            "Limit",
            "Rollover start"
          ],
          "as": "copied"
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

# Copy previous budgets copy without parent recalculation

## Trigger

The User chooses Copy Previous for one selected calendar month.

## Outcome

For one empty selected month, the Product copies preceding Budget allocations and rollover settings into the target month while suppressing ordinary parent auto-management.
