---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits the force-sync lookback month count.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::advanced-settings"
        }
      }
    },
    {
      "text": "A lookback outside zero through twelve reports refusal without saving that setting.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::advanced-settings"
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

# Change advanced settings out of range

## Trigger

The User submits the force-sync lookback month count.

## Outcome

A lookback outside zero through twelve reports refusal without saving that setting.
