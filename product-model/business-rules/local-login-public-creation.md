---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "local-login",
      "effect": "creates",
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
          "fact": "Server local auth disabled",
          "is": false
        }
      ]
    }
  ]
}
---

# The configured authentication method gates Local login creation

The User performs the selected Local login creates operation only under the listed deployment settings. Proof validity remains an authentication constraint.
