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

# Delete budget

Remove a monthly allocation; parent deletion removes same-month children, while child deletion leaves the parent limit unchanged.
