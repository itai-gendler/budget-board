---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a setup token or API credential to establish a provider connection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::external-accounts"
        }
      }
    },
    {
      "text": "Invalid setup-token exchange, invalid access credential, empty API key or rejected provider response reports a connection error without establishing a validated connection.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::external-accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    }
  ]
}
---

# Connect external provider credential refused

## Trigger

The User submits a setup token or API credential to establish a provider connection.

## Outcome

Invalid setup-token exchange, invalid access credential, empty API key or rejected provider response reports a connection error without establishing a validated connection.
