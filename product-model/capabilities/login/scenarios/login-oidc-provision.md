---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses external Login and returns with a previously unknown identity.",
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
      "text": "The Product creates a confirmed User and OIDC login, with six default widgets: Dashboard widget instances, Accounts widget, Flows widget, Metric widget and Net-worth widget containing Net-worth group, Net-worth line and Net-worth category defaults. It establishes a session. Default-widget failure is logged and does not establish local registration’s rollback result.",
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
          "to": "Confirmed"
        },
        {
          "entity": "oidc-login",
          "effect": "creates",
          "facts": [
            "Provider association",
            "Provider subject"
          ],
          "with": "user"
        },
        {
          "entity": "two-factor-authentication",
          "effect": "creates",
          "facts": [
            "Authenticator key",
            "Enabled"
          ],
          "with": "user",
          "to": "Disabled"
        },
        {
          "entity": "dashboard-widget",
          "effect": "creates",
          "facts": [
            "Kind"
          ],
          "as": "uncategorized",
          "with": "user"
        },
        {
          "entity": "dashboard-widget",
          "effect": "creates",
          "facts": [
            "Kind"
          ],
          "as": "spending",
          "with": "user"
        },
        {
          "entity": "accounts-widget",
          "effect": "creates",
          "facts": [
            "Selected accounts"
          ],
          "with": "user"
        },
        {
          "entity": "flows-widget",
          "effect": "creates",
          "facts": [
            "Month count"
          ],
          "with": "user"
        },
        {
          "entity": "metric-widget",
          "effect": "creates",
          "facts": [
            "Title",
            "Value template",
            "Label template"
          ],
          "with": "user"
        },
        {
          "entity": "net-worth-widget",
          "effect": "creates",
          "facts": [
            "Groups"
          ],
          "with": "user"
        },
        {
          "entity": "net-worth-group",
          "effect": "creates",
          "facts": [
            "Order",
            "Lines"
          ],
          "with": "net-worth-widget"
        },
        {
          "entity": "net-worth-line",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ],
          "with": "net-worth-group"
        },
        {
          "entity": "net-worth-category",
          "effect": "creates",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
          ],
          "with": "net-worth-line"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Controllers/OidcController.cs#Callback"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Utils/ExternalUserProvisioningService.cs#ProvisionExternalUserAsync"
    }
  ]
}
---

# Login OIDC provision

## Trigger

The User chooses external Login and returns with a previously unknown identity.

## Outcome

The Product creates a confirmed User and OIDC login, with six default widgets: Dashboard widget instances, Accounts widget, Flows widget, Metric widget and Net-worth widget containing Net-worth group, Net-worth line and Net-worth category defaults. It establishes a session. Default-widget failure is logged and does not establish local registration’s rollback result.
