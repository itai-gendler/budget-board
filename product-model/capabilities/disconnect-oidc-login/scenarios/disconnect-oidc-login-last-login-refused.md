---
{
  "kind": "validation",
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
      "text": "Removing the final login method without a password is refused; the external association remains.",
      "kind": "condition",
      "entities": [],
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

# Disconnect OIDC login last login refused

## Trigger

The User confirms disconnection of the external login method.

## Outcome

Removing the final login method without a password is refused; the external association remains.
