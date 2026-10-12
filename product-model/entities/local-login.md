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

# Local login

Established during registration/password creation; association can also be repaired during successful Login. Password presence and local association are distinct.

## Information kept

- **Provider association** — Association identifying the login method.
- **Password credential** — Local password proof, which may be absent even when the local association exists.
