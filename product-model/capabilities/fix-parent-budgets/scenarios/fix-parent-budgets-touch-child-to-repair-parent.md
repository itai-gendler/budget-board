---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Fix Parent for a child allocation requiring repair.",
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
      "text": "The Product resubmits child Budget.Limit and Rollover start unchanged so ordinary editing creates or raises the parent Budget to its child-total floor.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "changes",
          "facts": [
            "Limit",
            "Rollover start"
          ],
          "as": "child"
        },
        {
          "entity": "budget",
          "effect": "changes",
          "facts": [
            "Limit"
          ],
          "as": "existing-parent"
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
          "as": "missing-parent"
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

# Fix parent budgets touch child to repair parent

## Trigger

The User chooses Fix Parent for a child allocation requiring repair.

## Outcome

The Product resubmits child Budget.Limit and Rollover start unchanged so ordinary editing creates or raises the parent Budget to its child-total floor.
