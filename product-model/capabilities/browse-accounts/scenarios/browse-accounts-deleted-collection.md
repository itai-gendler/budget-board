---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the deleted financial-record collection to inspect retained names and deletion dates.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-accounts"
        }
      }
    },
    {
      "text": "The Product presents deleted Account names, sources and deletion markers for recovery or permanent removal.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name",
            "Source",
            "Deletion date"
          ]
        },
        {
          "entity": "institution",
          "effect": "reads",
          "facts": [
            "Name"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs"
    }
  ]
}
---

# Browse accounts deleted collection

## Trigger

The User opens the deleted financial-record collection to inspect retained names and deletion dates.

## Outcome

The Product presents deleted Account names, sources and deletion markers for recovery or permanent removal.
