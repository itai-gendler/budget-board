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

# Link external account

Connect a discovered provider record to an existing or inline-created local Account, change source and reset synchronization state while returning any former link to Manual.
