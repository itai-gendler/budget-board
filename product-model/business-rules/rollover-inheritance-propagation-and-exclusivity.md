---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "budget",
      "effect": "creates",
      "facts": [
        "Category",
        "Month",
        "Rollover start"
      ]
    },
    {
      "type": "entity",
      "id": "budget",
      "effect": "changes",
      "facts": [
        "Category",
        "Month",
        "Rollover start"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#HasRolloverConflict"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#UpdateBudgetAsync"
    }
  ]
}
---

# Rollover inheritance propagates without simultaneous parent and child rollover

Earlier setting inherited and propagated forward; creation drops conflicts, edits refuse them.
