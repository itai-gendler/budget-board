---
{
  "entities": [
    {
      "entity": "category",
      "shows": [
        "Name",
        "Parent",
        "Classification"
      ],
      "collects": [
        "Name",
        "Parent",
        "Classification"
      ]
    },
    {
      "entity": "user-settings",
      "shows": [
        "Built-in categories disabled"
      ],
      "collects": [
        "Built-in categories disabled"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionCategoryService.cs"
    }
  ]
}
---

# Categories

Effective vocabulary and custom categories. Shows and collects Name, Parent, Classification and built-in availability setting.
