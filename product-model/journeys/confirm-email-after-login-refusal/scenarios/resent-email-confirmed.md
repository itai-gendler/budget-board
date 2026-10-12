---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User requests a new confirmation email after the unconfirmed-email refusal.",
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
      "text": "The Product reads User.Email and sends a new confirmation link for that existing address. Following it begins Confirm email.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "reads",
          "facts": [
            "Email"
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
      "text": "The User follows the emailed confirmation link.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::confirm-email"
        }
      },
      "capability": "confirm-email"
    },
    {
      "text": "Valid confirmation proof changes User.Email confirmed to true and reports confirmed email.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "changes",
          "facts": [
            "Email confirmed"
          ],
          "from": "Unconfirmed",
          "to": "Confirmed"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::confirm-email"
        }
      },
      "capability": "confirm-email"
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

# Resent email confirmed

## Trigger

Confirm the existing address after a Login refusal.

## Outcome

The resent confirmation link confirms the same email.
