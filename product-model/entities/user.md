---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ApplicationUserService.cs"
    }
  ],
  "relations": [
    {
      "entity": "local-login",
      "verb": "owns",
      "cardinality": "one-to-one"
    },
    {
      "entity": "oidc-login",
      "verb": "owns",
      "cardinality": "one-to-one"
    },
    {
      "entity": "two-factor-authentication",
      "verb": "owns",
      "cardinality": "one-to-one"
    },
    {
      "entity": "recovery-code",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "user-settings",
      "verb": "owns",
      "cardinality": "one-to-one"
    },
    {
      "entity": "institution",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "account",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "account-type",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "asset",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "asset-type",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "tag",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "category",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "automatic-rule",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "recurring-transaction",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "budget",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "goal",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "simplefin-connection",
      "verb": "owns",
      "cardinality": "one-to-one"
    },
    {
      "entity": "simplefin-organization",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "simplefin-account",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "lunchflow-connection",
      "verb": "owns",
      "cardinality": "one-to-one"
    },
    {
      "entity": "lunchflow-account",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "transaction-import",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "dashboard-widget",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "accounts-widget",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "flows-widget",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "metric-widget",
      "verb": "owns",
      "cardinality": "one-to-many"
    },
    {
      "entity": "net-worth-widget",
      "verb": "owns",
      "cardinality": "one-to-many"
    }
  ],
  "kind": "person",
  "acts": "external"
}
---

# User

A person who uses Budget Board, with retained email confirmation, authentication-failure and synchronization facts.

## Information kept

- **Email** — Address used for identity, confirmation and recovery.
- **Email confirmed** — Whether confirmation has completed.
- **Failed sign-in count** — Retained failed-authentication count.
- **Lockout end** — Time until which authentication is locked.
- **Last sync** — Most recent recorded synchronization time.

## States

### Unconfirmed

Email confirmation has not completed.

### Confirmed

Email confirmation has completed.
