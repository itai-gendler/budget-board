---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits currency, decimal places, language or date-format selections.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::user-settings"
        }
      }
    },
    {
      "text": "The Product lazily creates User settings and its Untrained Auto categorizer configuration when absent.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "creates",
          "facts": [
            "Currency",
            "Decimal places",
            "Language",
            "Date format",
            "Budget warning threshold",
            "Force-sync lookback months",
            "Built-in account types disabled",
            "Built-in asset types disabled",
            "Built-in categories disabled",
            "Auto categorizer enabled",
            "Minimum probability percentage"
          ]
        },
        {
          "entity": "auto-categorizer",
          "effect": "creates",
          "facts": [
            "Trained classifier",
            "Training date",
            "Training start",
            "Training end"
          ],
          "with": "user-settings",
          "to": "Untrained"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::user-settings"
        }
      }
    },
    {
      "text": "The Product initializes missing User settings with USD, precision two, default Language and Date format, warning eighty, lookback zero, enabled built-ins, disabled categorizer and threshold seventy. Its contained classifier begins Untrained. Supplied Currency, Decimal places, Language and Date format selections are saved after validation.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Currency",
            "Decimal places",
            "Language",
            "Date format"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::user-settings"
        }
      }
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

# Change user settings format and language

## Trigger

The User submits currency, decimal places, language or date-format selections.

## Outcome

The Product initializes missing User settings with USD, precision two, default Language and Date format, warning eighty, lookback zero, enabled built-ins, disabled categorizer and threshold seventy. Its contained Auto categorizer begins Untrained. Supplied Currency, Decimal places, Language and Date format selections are saved after validation.
