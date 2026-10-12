---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits an empty or conflicting type name or invalid parent.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::asset-types"
        }
      }
    },
    {
      "text": "An empty or conflicting effective name or invalid parent reports refusal without saving the requested type entry.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::asset-types"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetTypeService.cs"
    }
  ]
}
---

# Add asset type name or parent conflict

## Trigger

The User submits an empty or conflicting type name or invalid parent.

## Outcome

An empty or conflicting effective name or invalid parent reports refusal without saving the requested type entry.
