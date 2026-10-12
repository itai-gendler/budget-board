---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "user",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "local-login",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "local-login",
      "effect": "changes"
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

# Local registration requires valid email and a password of at least three characters

Valid, unique email; local password minimum length three, with configured complexity requirements disabled.
