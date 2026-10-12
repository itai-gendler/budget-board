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

# Fix parent budgets

Repair parent allocations by resubmitting the child allocation.
