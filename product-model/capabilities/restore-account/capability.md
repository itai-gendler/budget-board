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
      "target": "server/BudgetBoard.Service/AccountService.cs"
    }
  ],
  "domain": "deleted-accounts"
}
---

# Restore account

Clear Account and Institution deletion markers while leaving Transactions deleted and retaining lost type/provider associations.
