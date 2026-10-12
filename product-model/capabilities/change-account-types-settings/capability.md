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
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    }
  ],
  "domain": "account-types"
}
---

# Change account types settings

Disable or reenable built-in Account types; disabling clears corresponding references and parents, while reenable refuses custom-name conflicts.
