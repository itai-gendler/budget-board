---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits invalid current proof, invalid authenticator verification or an invalid replacement password.",
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
      "text": "Invalid current proof, invalid new password or invalid enable proof reports refusal without applying the requested credential change.",
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

# Change security settings invalid proof or password

## Trigger

The User submits invalid current proof, invalid authenticator verification or an invalid replacement password.

## Outcome

Invalid current proof, invalid new password or invalid enable proof reports refusal without applying the requested credential change.
