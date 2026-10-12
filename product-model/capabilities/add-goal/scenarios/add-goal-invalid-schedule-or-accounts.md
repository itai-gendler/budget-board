---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits missing or conflicting schedule inputs, zero contribution, a past date or invalid linked-record selection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::add-goal"
        }
      }
    },
    {
      "text": "Missing schedule, both schedule choices, zero creation contribution, past target date or missing or invalid linked-record selection reports refusal. The browser is stricter about positive contribution; server creation does not universally reject negative input.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::add-goal"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs"
    }
  ]
}
---

# Add goal invalid schedule or accounts

## Trigger

The User submits missing or conflicting schedule inputs, zero contribution, a past date or invalid linked-record selection.

## Outcome

Missing schedule, both schedule choices, zero creation contribution, past target date or missing/invalid selected accounts reports refusal. The browser is stricter about positive contribution; server creation does not universally reject negative values.
