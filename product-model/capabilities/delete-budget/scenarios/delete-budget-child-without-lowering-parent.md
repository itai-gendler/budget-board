---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of a selected monthly allocation.",
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
      "text": "The Product removes the child Budget while leaving the parent Budget.Limit unchanged.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "removes",
          "as": "child"
        },
        {
          "entity": "budget",
          "effect": "reads",
          "facts": [
            "Limit"
          ],
          "as": "parent"
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

# Delete budget child without lowering parent

## Trigger

The User confirms removal of a selected monthly allocation.

## Outcome

The Product removes the child Budget while leaving the parent Budget.Limit unchanged.
