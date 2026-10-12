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
      "target": "server/BudgetBoard.Service/TransactionCategoryService.cs"
    }
  ],
  "domain": "categories"
}
---

# Change categories settings

Disable or reenable built-in transaction categories; disabling clears their actual financial references and reenable refuses conflicting custom names.
