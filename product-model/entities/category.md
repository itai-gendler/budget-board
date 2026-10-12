---
{
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

# Category

Custom lifecycle. Built-in categories and their classifications remain vocabulary.

## Information kept

- **Name** — Name used to present or select this instance.
- **Parent** — Parent vocabulary name, when supplied.
- **Classification** — Income, expense or transfer classification, inherited from a valid parent when applicable.
