---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to the selected definition’s identifiers, destination selection, cadence, bounds or amount settings.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
    },
    {
      "text": "Invalid cadence, bounds or linked-record selection reports refusal without applying the requested recurring edit.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/RecurringRuleService.cs"
    }
  ]
}
---

# Edit recurring transaction invalid cadence or bounds

## Trigger

The User submits changes to the selected definition’s identifiers, account selection, cadence, bounds or amount settings.

## Outcome

Invalid cadence, bounds or account reports refusal without applying the requested recurring edit.
