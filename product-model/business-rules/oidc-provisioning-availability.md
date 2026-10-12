---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "user",
      "effect": "creates",
      "contexts": [
        {
          "place": "web::public"
        }
      ],
      "to": "Confirmed"
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
          "fact": "Server new users disabled",
          "is": false
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

# The configured authentication method gates User creation

The User performs the selected User creates operation only under the listed deployment settings. Proof validity remains an authentication constraint.
