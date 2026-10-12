---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User follows the emailed confirmation link.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::confirm-email"
        }
      }
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

# Confirm email valid link

## Trigger

The User follows the emailed confirmation link.

## Outcome

Valid confirmation proof changes User.Email confirmed to true and reports confirmed email.
