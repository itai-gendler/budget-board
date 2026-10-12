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

# Remove external provider

Remove connection credentials and discovered provider records, returning linked Accounts to Manual while preserving local history.
