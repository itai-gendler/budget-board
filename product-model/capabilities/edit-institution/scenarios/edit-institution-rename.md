---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a replacement organization name.",
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
      "text": "The Product changes Institution.Name after name validation.",
      "kind": "product",
      "entities": [
        {
          "entity": "institution",
          "effect": "changes",
          "facts": [
            "Name"
          ]
        }
      ],
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

# Edit institution rename

## Trigger

The User submits a replacement organization name.

## Outcome

The Product changes Institution.Name after name validation.
