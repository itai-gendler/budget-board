---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User enters an organization name and submits creation.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    },
    {
      "text": "Empty or case-insensitively duplicate name, including a deleted-name match, reports refusal rather than restoring the existing record.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/InstitutionService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Controllers/InstitutionController.cs"
    }
  ]
}
---

# Add institution invalid name

## Trigger

The User enters an organization name and submits creation.

## Outcome

Empty or case-insensitively duplicate name, including a deleted-name match, reports refusal rather than restoring the existing record.
