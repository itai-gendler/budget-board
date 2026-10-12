---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits merchant, classification, cadence, bounds and amount settings for a selected destination.",
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
      "text": "Invalid cadence, nonpositive interval, excessive per-unit count, reversed bounds or invalid linked-record selection reports refusal without creating a definition.",
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

# Add recurring transaction invalid cadence or bounds

## Trigger

The User submits merchant, classification, cadence, bounds and amount settings for a selected account.

## Outcome

Invalid cadence, nonpositive interval, excessive per-unit count, reversed bounds or invalid account reports refusal without creating a definition.
