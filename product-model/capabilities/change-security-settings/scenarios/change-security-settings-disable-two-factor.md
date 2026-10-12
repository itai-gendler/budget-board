---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Disable for the enabled authenticator method.",
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
      "text": "The Product disables Two-factor authentication, resets its Authenticator key and replaces Recovery code credentials. Remembered-machine authentication is forgotten.",
      "kind": "product",
      "entities": [
        {
          "entity": "two-factor-authentication",
          "effect": "changes",
          "facts": [
            "Enabled",
            "Authenticator key"
          ],
          "from": "Enabled",
          "to": "Disabled"
        },
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

# Change security settings disable two factor

## Trigger

The User chooses Disable for the enabled authenticator method.

## Outcome

The Product disables Two-factor authentication, resets its Authenticator key and replaces Recovery code credentials. Remembered-machine authentication is forgotten.
