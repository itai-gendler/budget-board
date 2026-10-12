---
{
  "entities": [
    {
      "entity": "user",
      "shows": [
        "Email"
      ]
    },
    {
      "entity": "local-login",
      "collects": [
        "Password credential"
      ]
    },
    {
      "entity": "oidc-login",
      "shows": [
        "Provider association"
      ]
    },
    {
      "entity": "two-factor-authentication",
      "shows": [
        "Authenticator key",
        "Enabled"
      ],
      "collects": [
        "Enabled"
      ]
    },
    {
      "entity": "recovery-code",
      "shows": [
        "Credential"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ApplicationUserService.cs"
    }
  ]
}
---

# Security

Login-method information and credential settings. Shows email, method presence, authenticator key/status and newly generated recovery credentials. Collects credential/settings changes; proof is temporary input.
