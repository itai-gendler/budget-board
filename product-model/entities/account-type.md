---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    }
  ],
  "domain": "account-types"
}
---

# Account type

Custom entries are created, changed and removed. Built-in types remain vocabulary.

## Information kept

- **Name** — Name used to present or select this instance.
- **Parent** — Parent vocabulary name, when supplied.
- **Classification** — Asset or liability classification, inherited from a valid parent when applicable.
