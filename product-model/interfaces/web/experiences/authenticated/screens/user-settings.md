---
{
  "entities": [
    {
      "entity": "user-settings",
      "shows": [
        "Currency",
        "Decimal places",
        "Language",
        "Date format"
      ],
      "collects": [
        "Currency",
        "Decimal places",
        "Language",
        "Date format"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/UserSettingsService.cs"
    }
  ]
}
---

# User settings

Shows and collects Currency, Decimal places, Language and Date format.
