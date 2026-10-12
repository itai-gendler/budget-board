---
{
  "kind": "primary",
  "result": "achieved",
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
      },
      "capability": "register"
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
      },
      "capability": "register"
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
      },
      "capability": "register"
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
      },
      "capability": "register"
    },
    {
      "text": "The User follows the emailed confirmation link.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::confirm-email"
        }
      },
      "capability": "confirm-email"
    },
    {
      "text": "Valid confirmation proof changes User.Email confirmed to true and reports confirmed email.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "changes",
          "facts": [
            "Email confirmed"
          ],
          "from": "Unconfirmed",
          "to": "Confirmed"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::confirm-email"
        }
      },
      "capability": "confirm-email"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Unauthorized/Welcome.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
    }
  ]
}
---

# Registered email confirmed

## Trigger

Confirm the newly registered email.

## Outcome

Following the registration email confirms that address.
