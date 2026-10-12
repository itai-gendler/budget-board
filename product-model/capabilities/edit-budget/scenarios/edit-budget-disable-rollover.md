---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User clears the beginning month to disable entering rollover.",
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
      "text": "The Product clears the Budget.Rollover start and propagates that input to existing future classification records after parent/child exclusivity checks.",
      "kind": "product",
      "entities": [
        {
          "entity": "budget",
          "effect": "changes",
          "facts": [
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

# Edit budget disable rollover

## Trigger

The User clears the beginning month to disable entering rollover.

## Outcome

The Product clears the Budget.Rollover start and propagates that value to existing future category records after parent/child exclusivity checks.
