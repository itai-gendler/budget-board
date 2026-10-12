---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "removes",
      "contexts": [
        {
          "place": "web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/LunchFlowAccountService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "owns",
          "entity": "user"
        }
      ]
    }
  ]
}
---

# Only the owning User removes LunchFlow account

The owning User may remove LunchFlow account through the declared ownership path in the authenticated Experience.
