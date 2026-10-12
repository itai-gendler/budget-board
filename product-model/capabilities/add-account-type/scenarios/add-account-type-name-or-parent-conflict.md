---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a type name, optional parent and Classification.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-types"
        }
      }
    },
    {
      "text": "An empty or conflicting effective name, invalid parent or invalid classification reports refusal without adding the entry.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-types"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    }
  ]
}
---

# Add account type name or parent conflict

## Trigger

The User submits a type name, optional parent and asset/liability classification.

## Outcome

An empty or conflicting effective name, invalid parent or invalid classification reports refusal without adding the entry.
