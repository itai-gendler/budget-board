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
        "Sale price"
      ]
    },
    {
      "entity": "value",
      "shows": [
        "Date",
        "Amount"
      ],
      "collects": [
        "Date",
        "Amount"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ValueService.cs"
    }
  ]
}
---

# Asset details

Selected Asset and dated Values. Shows and collects editable Asset facts and Value.Date/Amount.
