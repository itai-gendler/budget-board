---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms disconnection of the external login method.",
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
      "text": "With a password or another remaining login method, the Product removes OIDC login.",
      "kind": "product",
      "entities": [
        {
          "entity": "oidc-login",
          "effect": "removes"
        },
        {
          "entity": "local-login",
          "effect": "reads",
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

# Disconnect OIDC login remove login

## Trigger

The User confirms disconnection of the external login method.

## Outcome

With a password or another remaining login method, the Product removes OIDC login.

## Edge cases

- A demo-filter refusal leaves the login association unchanged.
