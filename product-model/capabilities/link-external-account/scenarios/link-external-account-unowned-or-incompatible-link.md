---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects an existing local record or creates one inline and submits the provider link.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::external-accounts"
        }
      }
    },
    {
      "text": "Invalid provider/local selection or incompatible requested link reports refusal without changing the association.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::external-accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    }
  ]
}
---

# Link external account unowned or incompatible link

## Trigger

The User selects an existing local record or creates one inline and submits the provider link.

## Outcome

Invalid provider/local selection or incompatible requested link reports refusal without changing the association.
