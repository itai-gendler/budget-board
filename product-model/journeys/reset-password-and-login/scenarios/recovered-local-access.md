---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User requests a reset code for the entered email.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "reset-password"
    },
    {
      "text": "The Product reads User.Email and Email confirmed and sends a reset code only for a confirmed address. The request response does not disclose whether the address exists.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "reads",
          "facts": [
            "Email",
            "Email confirmed"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "reset-password"
    },
    {
      "text": "The User enters the emailed reset code and a replacement password.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "web": {
          "place": "web::public::reset-password"
        }
      },
      "capability": "reset-password"
    },
    {
      "text": "The Product validates the reset code and replaces the Local login Password credential, then returns the User to Login.",
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
          "place": "web::public::login"
        }
      },
      "capability": "reset-password"
    },
    {
      "text": "The User submits the email and password to establish a session.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "login"
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
      },
      "capability": "login"
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
      },
      "capability": "login"
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
      },
      "capability": "login"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Unauthorized/Welcome.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
    }
  ]
}
---

# Recovered local access

## Trigger

Recover local access.

## Outcome

A reset code establishes the replacement password and returned Login establishes a session.
