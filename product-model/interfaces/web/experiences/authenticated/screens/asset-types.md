---
{
  "entities": [
    {
      "entity": "asset-type",
      "shows": [
        "Name",
        "Parent"
      ],
      "collects": [
        "Name",
        "Parent"
      ]
    },
    {
      "entity": "user-settings",
      "shows": [
        "Built-in asset types disabled"
      ],
      "collects": [
        "Built-in asset types disabled"
      ]
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

# Asset types

Effective vocabulary and custom types. Shows and collects Name, Parent and built-in availability setting.
