---
{
  "entities": [
    {
      "entity": "auto-categorizer",
      "shows": [
        "Training date",
        "Training start",
        "Training end"
      ]
    },
    {
      "entity": "user-settings",
      "shows": [
        "Auto categorizer enabled",
        "Minimum probability percentage"
      ],
      "collects": [
        "Auto categorizer enabled",
        "Minimum probability percentage"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    }
  ]
}
---

# Auto categorizer

Training status/range and activation settings. Shows training dates/state. Collects enabled setting and probability threshold.
