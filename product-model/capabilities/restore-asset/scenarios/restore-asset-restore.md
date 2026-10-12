---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Restore for the selected deleted financial property record.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-assets"
        }
      }
    },
    {
      "text": "The Product clears Asset.Deletion date without reconstructing its previous type.",
      "kind": "product",
      "entities": [
        {
          "entity": "asset",
          "effect": "changes",
          "facts": [
            "Deletion date"
          ],
          "from": "Deleted",
          "to": "Active"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-assets"
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

# Restore asset restore

## Trigger

The User chooses Restore for the selected deleted financial property record.

## Outcome

The Product clears Asset.Deletion date without reconstructing its previous type.
