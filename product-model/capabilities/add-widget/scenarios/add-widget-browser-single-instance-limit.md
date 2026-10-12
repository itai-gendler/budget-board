---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the picker while a restricted single-instance summary type is already present.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "The browser offers no second single-instance summary while that Kind is present. The server creation operation does not enforce the same maximum.",
      "kind": "condition",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    }
  ]
}
---

# Add widget browser single instance limit

## Trigger

The User opens the picker while a restricted single-instance summary type is already present.

## Outcome

The browser offers no second Uncategorized transactions, Spending trends or Flows summary while that type is present. Creation through the server does not enforce the same maximum.
