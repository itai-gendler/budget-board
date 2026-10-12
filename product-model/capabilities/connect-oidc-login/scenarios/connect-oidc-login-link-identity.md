---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Connect and completes external identity proof.",
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
      "text": "Validated external subject and matching email create the OIDC login association.",
      "kind": "product",
      "entities": [
        {
          "entity": "oidc-login",
          "effect": "creates",
          "facts": [
            "Provider association",
            "Provider subject"
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

# Connect OIDC login link identity

## Trigger

The User chooses Connect and completes external identity proof.

## Outcome

Validated external subject and matching email create the OIDC login association.
