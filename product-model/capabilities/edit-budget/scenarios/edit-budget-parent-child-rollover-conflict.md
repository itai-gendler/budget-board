---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits rollover that conflicts with an existing parent or child setting.",
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
      "text": "An edit enabling overlapping parent and child rollover reports refusal; creation’s conflict-drop behavior is not applied to this edit.",
      "kind": "condition",
      "entities": [],
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

# Edit budget parent child rollover conflict

## Trigger

The User submits rollover that conflicts with an existing parent or child setting.

## Outcome

An edit enabling overlapping parent and child rollover reports refusal; creation’s conflict-drop behavior is not applied to this edit.
