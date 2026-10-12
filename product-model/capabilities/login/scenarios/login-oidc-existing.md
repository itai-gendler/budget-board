---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses external Login and returns with an identity already associated with the existing email.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      }
    },
    {
      "text": "The Product reads User and the bound OIDC login.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "reads",
          "facts": [
            "Email",
            "Email confirmed",
            "Failed sign-in count",
            "Lockout end"
          ]
        },
        {
          "entity": "oidc-login",
          "effect": "reads",
          "facts": [
            "Provider association",
            "Provider subject"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      }
    },
    {
      "text": "Matching external identity method association and a successful external exchange establish a session without invoking local second-factor authentication.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Controllers/OidcController.cs#Callback"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Utils/ExternalUserProvisioningService.cs#ProvisionExternalUserAsync"
    }
  ]
}
---

# Login OIDC existing

## Trigger

The User chooses external Login and returns with an identity already associated with the existing email.

## Outcome

Matching OIDC login association and a successful external exchange establish a session without invoking local second-factor authentication.
