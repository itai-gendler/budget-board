---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "two-factor-authentication",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "two-factor-authentication",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "recovery-code",
      "effect": "creates"
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

# Second-factor configuration retains key and recovery-credential lifecycle effects

Key initialization/reset, enable proof, disabling and replacement of ten recovery codes retain their observed effects.
