---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the email and password to establish a session.",
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
      "text": "The Product reads User and the supplied local proof.",
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
          "entity": "local-login",
          "effect": "reads",
          "facts": [
            "Provider association",
            "Password credential"
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
      "text": "Valid password proof establishes a session, subject to confirmation and lockout checks. The remember-me choice affects cookie persistence.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      }
    },
    {
      "text": "After successful password-based authentication, the Product repairs a missing Local login provider association while retaining the Password credential.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "local-login",
          "effect": "changes",
          "facts": [
            "Provider association"
          ]
        }
      ],
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
    }
  ]
}
---

# Login password

## Trigger

The User submits the email and password to establish a session.

## Outcome

Valid password proof establishes a session, subject to confirmation and lockout checks. The remember-me choice affects cookie persistence.

## Edge cases

- A successful password Login can repair a missing local provider association.
