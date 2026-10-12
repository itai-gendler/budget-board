---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits authenticator verification and chooses Enable.",
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
      "text": "The Product initializes a missing Two-factor authentication Authenticator key for setup.",
      "kind": "product",
      "entities": [
        {
          "entity": "two-factor-authentication",
          "effect": "changes",
          "facts": [
            "Authenticator key"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::security"
        }
      }
    },
    {
      "text": "Valid authenticator proof enables Two-factor authentication. The browser request replaces any existing Recovery code credentials with ten new credentials and forgets remembered-machine authentication.",
      "kind": "product",
      "entities": [
        {
          "entity": "two-factor-authentication",
          "effect": "changes",
          "facts": [
            "Enabled"
          ],
          "from": "Disabled",
          "to": "Enabled"
        },
        {
          "entity": "recovery-code",
          "effect": "creates",
          "facts": [
            "Credential"
          ],
          "as": "new-codes"
        },
        {
          "entity": "recovery-code",
          "effect": "removes",
          "as": "old-codes"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Settings/SettingsSecurity/TwoFactorAuth/TwoFactorAuth.tsx#TwoFactorAuth"
    }
  ]
}
---

# Change security settings enable two factor

## Trigger

The User submits authenticator verification and chooses Enable.

## Outcome

Valid authenticator proof enables Two-factor authentication. The browser request replaces any existing Recovery code credentials with ten new credentials and forgets remembered-machine authentication.
