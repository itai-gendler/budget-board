---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-account",
      "effect": "removes",
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

# Demo mode closes selected SimpleFIN account removal

The owning User performs the selected SimpleFIN account removes operation only when server Demo mode is false. These selectors retain the actual operation and place boundary.
