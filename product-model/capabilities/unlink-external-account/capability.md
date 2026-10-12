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

# Unlink external account

Clear a discovered provider record’s local link and Last sync, returning the former linked Account to Manual source.
