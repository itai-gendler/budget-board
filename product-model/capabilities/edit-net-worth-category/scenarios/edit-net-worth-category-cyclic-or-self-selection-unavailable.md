---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User attempts to select a self-reference or cycle-producing source name.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::widget-settings"
        }
      }
    },
    {
      "text": "The browser omits self-references and cycle-producing line choices. Exact-case server Line/Name validation rejects a missing target or direct reciprocal dependency; the lowercase browser payload and recursive renderer do not establish a universal server cycle guarantee.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::widget-settings"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/widgets.ts"
    }
  ]
}
---

# Edit net worth category cyclic or self selection unavailable

## Trigger

The User attempts to select a self-reference or cycle-producing source name.

## Outcome

The browser omits self-references and cycle-producing line choices. Exact-case server Line/Name validation rejects a missing target or direct reciprocal dependency; the lowercase browser payload and recursive renderer do not establish a universal server cycle guarantee.
