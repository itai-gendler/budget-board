---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction-import",
      "effect": "creates",
      "contexts": [
        {
          "place": "web::authenticated::import-transactions"
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

# Demo mode closes selected Transaction import creation

The owning User performs the selected Transaction import creates operation only when server Demo mode is false. These selectors retain the actual operation and place boundary.
