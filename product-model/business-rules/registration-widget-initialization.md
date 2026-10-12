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
      "id": "dashboard-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "accounts-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "flows-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "metric-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "creates"
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

# Registration initializes six widgets with method-specific failure outcomes

Six default widgets; local initialization failure attempts rollback; OIDC initialization failure does not establish the same rollback result.
