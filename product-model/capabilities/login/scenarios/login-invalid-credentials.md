---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an invalid password or second-factor proof.",
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
      "text": "Invalid password or second-factor proof reports authentication failure. Failed proof can change the User failed-sign-in count and lockout end; no session is established.",
      "kind": "condition",
      "entities": [
        {
          "entity": "user",
          "effect": "changes",
          "facts": [
            "Failed sign-in count",
            "Lockout end"
          ]
        }
      ],
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
    }
  ]
}
---

# Login invalid credentials

## Trigger

The User submits an invalid password or second-factor proof.

## Outcome

Invalid password or second-factor proof reports authentication failure. Failed proof can change the User failed-sign-in count and lockout end; no session is established.
