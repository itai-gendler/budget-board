---
{
  "kind": "validation",
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
      "text": "Unsupported currency, locale or date format, or precision outside zero through three, reports refusal without saving the requested selection.",
      "kind": "condition",
      "entities": [],
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

# Change user settings invalid choice

## Trigger

The User submits currency, decimal places, language or date-format selections.

## Outcome

Unsupported currency, locale or date format, or precision outside zero through three, reports refusal without saving the requested selection.
