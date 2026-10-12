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
      "text": "The Product saves child Budget.Limit and Rollover start; an existing parent Budget is raised to the total child floor or a missing parent Budget is created.",
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

# Edit budget child parent repair

## Trigger

The User submits a replacement limit or rollover start for a selected monthly allocation.

## Outcome

The Product saves child Budget.Limit and Rollover start; an existing parent Budget is raised to the total child floor or a missing parent Budget is created.

## Decision points

### Does the same-month parent exist and cover the child total?

Does the same-month parent exist and cover the child total?

- Missing → create it from the child total.
- Existing below the child total → raise its Limit.
- Existing covering the total → retain its Limit.
