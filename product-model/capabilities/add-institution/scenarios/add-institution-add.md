---
{
  "kind": "primary",
  "routes": {
    "accounts": "Accounts",
    "external-accounts": "External accounts"
  },
  "steps": [
    {
      "text": "The User enters an organization name and submits creation.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "accounts": {
          "place": "web::authenticated::accounts"
        },
        "external-accounts": {
          "place": "web::authenticated::external-accounts"
        }
      }
    },
    {
      "text": "The Product creates Institution with the supplied Name, initial Order and no deletion marker.",
      "kind": "product",
      "entities": [
        {
          "entity": "institution",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Deletion date"
          ],
          "to": "Active"
        }
      ],
      "actor": "user",
      "contexts": {
        "accounts": {
          "place": "web::authenticated::accounts"
        },
        "external-accounts": {
          "place": "web::authenticated::external-accounts"
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

# Add institution add

## Trigger

The User enters an organization name and submits creation.

## Outcome

The Product creates Institution with the supplied Name, initial Order and no deletion marker.

## Edge cases

- A structural demo-filter refusal leaves the collection unchanged.
