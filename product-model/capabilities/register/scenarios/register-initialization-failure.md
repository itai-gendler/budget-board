---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User enters an email and password and submits registration.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::register"
        }
      }
    },
    {
      "text": "The Product creates the User before initialization.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "creates",
          "facts": [
            "Email",
            "Email confirmed",
            "Failed sign-in count",
            "Lockout end",
            "Last sync"
          ],
          "to": "Unconfirmed"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::register"
        }
      }
    },
    {
      "text": "Default widget initialization fails; registration reports failure and attempts deletion of the newly created User. Rollback failure is logged and can leave partial initialization.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "removes",
          "from": "Unconfirmed"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::register"
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

# Register initialization failure

## Trigger

The User enters an email and password and submits registration.

## Outcome

Default widget initialization fails; registration reports failure and attempts deletion of the newly created User. Rollback failure is logged and can leave partial initialization.
