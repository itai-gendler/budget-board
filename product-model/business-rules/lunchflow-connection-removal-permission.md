---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "lunchflow-connection",
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
      "target": "server/BudgetBoard.Service/LunchFlowService.cs"
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

# Only the owning User removes LunchFlow connection

The owning User may remove LunchFlow connection through the declared ownership path in the authenticated Experience.
