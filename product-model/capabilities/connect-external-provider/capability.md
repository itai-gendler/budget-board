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

# Connect external provider

Validate SimpleFIN setup-token exchange or LunchFlow API credentials, retain the connection and discover provider records; later discovery errors can leave credentials retained.
