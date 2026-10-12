---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User requests ten replacement recovery credentials.",
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
      "text": "The Product removes previous Recovery code credentials and generates ten replacement credentials for the enabled method.",
      "kind": "product",
      "entities": [
        {
          "entity": "recovery-code",
          "effect": "removes",
          "as": "old-codes"
        },
        {
          "entity": "recovery-code",
          "effect": "creates",
          "facts": [
            "Credential"
          ],
          "as": "new-codes"
        }
      ],
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

# Change security settings replace recovery codes

## Trigger

The User requests ten replacement recovery credentials.

## Outcome

The Product removes previous Recovery code credentials and generates ten replacement credentials for the enabled method.
