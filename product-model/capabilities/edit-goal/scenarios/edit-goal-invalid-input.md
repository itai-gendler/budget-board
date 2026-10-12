---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an explicit nonpositive contribution, past date or conflicting combined schedule update.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::goal-details"
        }
      }
    },
    {
      "text": "Explicit nonpositive contribution, past date or invalid combined schedule update reports refusal. Partial nullable updates retain their narrower checks rather than a universal schedule invariant.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::goal-details"
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

# Edit goal invalid input

## Trigger

The User submits an explicit nonpositive contribution, past date or conflicting combined schedule update.

## Outcome

Explicit nonpositive contribution, past date or invalid combined schedule update reports refusal. Partial nullable updates retain their narrower checks rather than a universal schedule invariant.
