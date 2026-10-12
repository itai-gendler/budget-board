---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "user",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "user",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "local-login",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "two-factor-authentication",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "recovery-code",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "recovery-code",
      "effect": "removes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ApplicationUserService.cs"
    }
  ]
}
---

# Login validates its route proofs before establishing a session

Password, confirmation, lockout and second-factor/recovery checks follow their routes. Remember-me affects persistence; application cookie lifetime is thirty days with sliding expiration. OIDC does not imply local 2FA.
