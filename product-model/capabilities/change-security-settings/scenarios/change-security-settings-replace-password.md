---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits current proof and a replacement password.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::security"
        }
      }
    },
    {
      "text": "The Product validates current proof and replaces the Local login Password credential.",
      "kind": "product",
      "entities": [
        {
          "entity": "local-login",
          "effect": "changes",
          "facts": [
            "Password credential"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::security"
        }
      }
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Unauthorized/Welcome.tsx"
    }
  ]
}
---

# Change security settings replace password

## Trigger

The User submits current proof and a replacement password.

## Outcome

The Product validates current proof and replaces the Local login Password credential.
