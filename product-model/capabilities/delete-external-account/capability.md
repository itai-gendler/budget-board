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
      "target": "server/BudgetBoard.Service/SyncService.cs"
    }
  ],
  "domain": "external-accounts"
}
---

# Delete external account

Remove selected provider metadata and return a linked local Account to Manual source while retaining local financial history.
