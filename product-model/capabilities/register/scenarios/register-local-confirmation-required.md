---
{
  "kind": "primary",
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
      "text": "Deployment settings require email confirmation before local access.",
      "kind": "condition",
      "actor": "user",
      "entities": [
        {
          "entity": "deployment-settings",
          "effect": "reads",
          "facts": [
            "Email confirmation required"
          ]
        }
      ],
      "contexts": {
        "web": {
          "place": "web::public::register"
        }
      }
    },
    {
      "text": "The Product creates User, Local login and disabled Two-factor authentication with six default widgets: two Dashboard widget instances plus Accounts widget, Flows widget, Metric widget and Net-worth widget with Net-worth group, Net-worth line and Net-worth category defaults.",
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
        },
        {
          "entity": "local-login",
          "effect": "creates",
          "facts": [
            "Provider association",
            "Password credential"
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
          "place": "web::public::register"
        }
      }
    },
    {
      "text": "The Product emails the User a confirmation link; registration completes with confirmation required before password access.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "reads",
          "facts": [
            "Email"
          ]
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

# Register local confirmation required

## Trigger

The User enters an email and password and submits registration.

## Outcome

The Product emails the User a confirmation link; registration completes with confirmation required before password access.

## Edge cases

- A rejected initialization is reported rather than represented as an authenticated session.
