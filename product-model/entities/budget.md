---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#BudgetService"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Database/Data/UserDataContext.cs#OnModelCreating"
    }
  ],
  "domain": "budgets"
}
---

# Budget

Category/calendar-month record, created/copied, edited and removed.

## Information kept

- **Category** — Transaction-category name, identifying either a parent or a child allocation.
- **Month** — Date identifying a category/calendar-month Budget.
- **Limit** — Category allocation for that month.
- **Rollover start** — Optional beginning of accumulated budgeted-month remainders.
