---
{
  "availability": [
    {
      "place": "web::authenticated"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs"
    }
  ],
  "domain": "budgets"
}
---

# Add budget

Create category/calendar-month allocations, inheriting rollover and applying the creation-specific parent effects; valid entries can survive other batch refusals.
