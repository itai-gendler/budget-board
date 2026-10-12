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
      "text": "Deployment settings do not require email confirmation before local access.",
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
      "text": "Registration completes without a confirmation requirement and returns the User to Login.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "register"
    },
    {
      "text": "The User submits the email and password to establish a session.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "login"
    },
    {
      "text": "The Product reads User and the supplied local proof.",
      "kind": "product",
      "entities": [
        {
          "entity": "user",
          "effect": "reads",
          "facts": [
            "Email",
            "Email confirmed",
            "Failed sign-in count",
            "Lockout end"
          ]
        },
        {
          "entity": "local-login",
          "effect": "reads",
          "facts": [
            "Provider association",
            "Password credential"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "login"
    },
    {
      "text": "Valid password proof establishes a session, subject to confirmation and lockout checks. The remember-me choice affects cookie persistence.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "login"
    },
    {
      "text": "After successful password-based authentication, the Product repairs a missing Local login provider association while retaining the Password credential.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "local-login",
          "effect": "changes",
          "facts": [
            "Provider association"
          ]
        }
      ],
      "contexts": {
        "web": {
          "place": "web::public::login"
        }
      },
      "capability": "login"
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

# Registered local access

## Trigger

Establish local access.

## Outcome

Registration and subsequent Login establish a session.
