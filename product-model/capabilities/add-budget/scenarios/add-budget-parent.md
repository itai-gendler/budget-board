---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a parent classification, calendar month and limit, including a limit below existing child allocations.",
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
      "text": "The Product creates the parent Budget with the entered classification, calendar month and limit and the effective rollover setting. Creation does not apply the child-total floor used by parent editing.",
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Budgets/BudgetsToolbar/AddBudget/AddBudget.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#TryAddBudget"
    }
  ]
}
---

# Add budget parent

## Trigger

The User submits a parent category, calendar month and limit, including a limit below existing child allocations.

## Outcome

The Product creates the parent Budget with the entered category, calendar month and limit and the effective rollover setting. Creation does not apply the child-total floor used by parent editing.
