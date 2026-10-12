---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "user-settings",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "user-settings",
      "effect": "changes"
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

# Personal settings use the shipped defaults and supported value ranges

Defaults: USD, precision two, default language/date format, warning eighty, lookback zero, built-ins enabled, categorizer off, threshold seventy. Precision 0–3, percentages 0–100, lookback 0–12 and supported choices are validated.
