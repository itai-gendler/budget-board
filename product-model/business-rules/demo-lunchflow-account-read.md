---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "reads",
      "contexts": [
        {
          "place": "web::authenticated::external-accounts"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Utils/DemoModeFilter.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "owns",
          "entity": "user"
        }
      ],
      "when": [
        {
          "entity": "deployment-settings",
          "fact": "Demo mode",
          "is": false
        }
      ]
    }
  ]
}
---

# Demo mode closes selected LunchFlow account read

The owning User performs the selected LunchFlow account reads operation only when server Demo mode is false. These selectors retain the actual operation and place boundary.
