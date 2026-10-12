---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to the selected type’s name, parent or Classification.",
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
      "text": "Conflicting effective name, invalid parent or invalid classification reports refusal without applying the requested vocabulary edit.",
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

# Edit account type name or parent conflict

## Trigger

The User submits changes to the selected type’s name, parent or asset/liability classification.

## Outcome

Conflicting effective name, invalid parent or invalid classification reports refusal without applying the requested vocabulary edit.
