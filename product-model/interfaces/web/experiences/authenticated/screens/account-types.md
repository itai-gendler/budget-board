---
{
  "entities": [
    {
      "entity": "account-type",
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
        "Built-in account types disabled"
      ],
      "collects": [
        "Built-in account types disabled"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    }
  ]
}
---

# Account types

Effective vocabulary and custom types. Shows and collects Name, Parent, Classification and built-in availability setting.
