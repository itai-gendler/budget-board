---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "lunchflow-connection",
      "effect": "creates",
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

# Demo mode closes selected LunchFlow connection creation

The owning User performs the selected LunchFlow connection creates operation only when server Demo mode is false. These selectors retain the actual operation and place boundary.
