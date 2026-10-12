---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "auto-categorizer",
      "effect": "reads",
      "contexts": [
        {
          "place": "web::authenticated"
        }
      ],
      "facts": [
        "Trained classifier"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/AutomaticTransactionCategorizerHelper.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "user-settings"
        },
        {
          "verb": "owns",
          "entity": "user"
        }
      ],
      "when": [
        {
          "entity": "user-settings",
          "fact": "Auto categorizer enabled",
          "is": true
        }
      ]
    },
    {
      "unattended": true,
      "when": [
        {
          "entity": "user-settings",
          "fact": "Auto categorizer enabled",
          "is": true
        }
      ]
    }
  ]
}
---

# Only enabled categorization reads the trained classifier

The owning User’s enabled setting permits classifier use, including shared unattended processing. Model presence and confidence are validated by the prediction behavior.
