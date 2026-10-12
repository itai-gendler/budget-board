---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a child classification, calendar month and positive limit.",
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
      "text": "The Product creates the child Budget. A missing parent Budget is created with the sum of that month’s child limits; a positive child limit increases an existing parent limit by that amount.",
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

# Add budget child and parent effect

## Trigger

The User submits a child classification, calendar month and positive limit.

## Outcome

The Product creates the child Budget. A missing parent Budget is created with the sum of that month’s child limits; a positive child limit increases an existing parent limit by that amount.

## Decision points

### Does a same-month parent allocation exist?

Does a same-month parent allocation exist?

- Missing → create the parent from children.
- Existing → increase its Limit by the positive child amount.
