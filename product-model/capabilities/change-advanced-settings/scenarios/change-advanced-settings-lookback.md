---
{
  "kind": "primary",
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
      "text": "The Product saves User settings.Force-sync lookback months from zero through twelve for provider history requests.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Force-sync lookback months"
          ]
        }
      ],
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

# Change advanced settings lookback

## Trigger

The User submits the force-sync lookback month count.

## Outcome

The Product saves User settings.Force-sync lookback months from zero through twelve for provider history requests.
