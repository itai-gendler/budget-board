---
{
  "entities": [
    {
      "entity": "asset",
      "shows": [
        "Name",
        "Type",
        "Purchase date",
        "Purchase price",
        "Sale date",
        "Sale price",
        "Hidden",
        "Order",
        "Deletion date"
      ],
      "collects": [
        "Name",
        "Type",
        "Purchase date",
        "Purchase price",
        "Sale date",
        "Sale price",
        "Hidden",
        "Order"
      ]
    },
    {
      "entity": "value",
      "shows": [
        "Date",
        "Amount"
      ]
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

# Assets

Asset collection. Shows and collects name, type, purchase/sale facts, visibility and order. Shows latest Value results.
