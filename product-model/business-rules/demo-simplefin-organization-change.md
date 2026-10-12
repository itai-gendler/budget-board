---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-organization",
      "effect": "changes",
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

# Demo mode closes selected SimpleFIN organization change

The owning User performs the selected SimpleFIN organization changes operation only when server Demo mode is false. These selectors retain the actual operation and place boundary.
