---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms deletion of the selected financial property record.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::assets"
        }
      }
    },
    {
      "text": "The Product marks Asset deleted and clears Type while retaining dated Value history.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "changes",
          "facts": [
            "Deletion date",
            "Type"
          ],
          "from": "Active",
          "to": "Deleted"
        },
        {
          "entity": "value",
          "effect": "reads",
          "facts": [
            "Date",
            "Amount"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::assets"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetService.cs"
    }
  ]
}
---

# Delete asset soft delete

## Trigger

The User confirms deletion of the selected financial property record.

## Outcome

The Product marks Asset deleted and clears Type while retaining dated Value history.
