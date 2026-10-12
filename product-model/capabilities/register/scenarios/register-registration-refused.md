---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an invalid email, duplicate email or invalid password.",
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
      "text": "Registration reports invalid email, duplicate email or invalid password; no new identity is established.",
      "kind": "condition",
      "entities": [],
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

# Register registration refused

## Trigger

The User submits an invalid email, duplicate email or invalid password.

## Outcome

Registration reports invalid email, duplicate email or invalid password; no new identity is established.
