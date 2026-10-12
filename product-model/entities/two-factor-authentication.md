---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ApplicationUserService.cs"
    }
  ]
}
---

# Two-factor authentication

Disabled, Enabled. Key initialization/reset and settings changes retain their actual effects.

## Information kept

- **Authenticator key** — Retained authenticator secret.
- **Enabled** — Whether authenticator verification is enabled.

## States

### Disabled

Authenticator verification is disabled.

### Enabled

Authenticator verification is enabled.
