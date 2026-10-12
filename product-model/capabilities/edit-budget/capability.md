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

# Edit budget

Change monthly allocation or rollover, with operation-specific parent checks and forward propagation.
