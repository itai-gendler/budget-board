---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an invalid reset code, unconfirmed email or invalid replacement password.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::reset-password"
        }
      }
    },
    {
      "text": "Invalid reset code, unconfirmed or missing address, or invalid replacement password reports refusal without changing the credential.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::reset-password"
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

# Reset password invalid proof or password

## Trigger

The User submits an invalid reset code, unconfirmed email or invalid replacement password.

## Outcome

Invalid reset code, unconfirmed or missing address, or invalid replacement password reports refusal without changing the credential.
