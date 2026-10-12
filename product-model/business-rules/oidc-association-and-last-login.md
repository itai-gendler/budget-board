---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "oidc-login",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "oidc-login",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "oidc-login",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "user",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "user",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "local-login",
      "effect": "reads"
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

# OIDC association and disconnection require matching identity and a remaining method

Existing association must match; same-email identity requires explicit connection. Disconnection checks password or a remaining login method.
