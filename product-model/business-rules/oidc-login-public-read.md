---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "oidc-login",
      "effect": "reads",
      "contexts": [
        {
          "place": "web::public"
        }
      ]
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
      "target": "server/BudgetBoard.WebAPI/Controllers/OidcController.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ApplicationUserService.cs"
    }
  ],
  "permits": [
    {
      "actors": [
        "user"
      ],
      "when": [
        {
          "entity": "deployment-settings",
          "fact": "Server OIDC enabled",
          "is": true
        },
        {
          "entity": "deployment-settings",
          "fact": "Demo mode",
          "is": false
        }
      ]
    }
  ]
}
---

# The configured authentication method gates OIDC login read

The User performs the selected OIDC login reads operation only under the listed deployment settings. Proof validity remains an authentication constraint.
