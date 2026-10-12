---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User enters a recovery credential after the password stage.",
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
        },
        {
          "entity": "two-factor-authentication",
          "effect": "reads",
          "facts": [
            "Authenticator key",
            "Enabled"
          ]
        },
        {
          "entity": "recovery-code",
          "effect": "reads",
          "facts": [
            "Credential"
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
      "text": "Valid password and recovery proof establish a session; the Product consumes the Recovery code.",
      "kind": "product",
      "entities": [
        {
          "entity": "recovery-code",
          "effect": "removes"
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

# Login recovery code

## Trigger

The User enters a recovery credential after the password stage.

## Outcome

Valid password and recovery proof establish a session and consume the Recovery code.

## Edge cases

- A successful password Login can repair a missing local provider association.
