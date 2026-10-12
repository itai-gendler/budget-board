---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens training status, training range and activation settings.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::auto-categorizer"
        }
      }
    },
    {
      "text": "The Product presents Auto categorizer training state and dates with User settings activation and probability threshold.",
      "kind": "product",
      "entities": [
        {
          "entity": "auto-categorizer",
          "effect": "reads",
          "facts": [
            "Training date",
            "Training start",
            "Training end"
          ]
        },
        {
          "entity": "user-settings",
          "effect": "reads",
          "facts": [
            "Auto categorizer enabled",
            "Minimum probability percentage"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::auto-categorizer"
        }
      }
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

# Browse auto categorizer training and settings

## Trigger

The User opens training status, training range and activation settings.

## Outcome

The Product presents Auto categorizer training state and dates with User settings activation and probability threshold.
