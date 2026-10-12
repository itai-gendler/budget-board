---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "value",
      "effect": "changes",
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
      "target": "server/BudgetBoard.Service/ValueService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "asset"
        },
        {
          "verb": "owns",
          "entity": "user"
        }
      ]
    }
  ]
}
---

# Only the owning User changes Value

The owning User may change Value through the declared ownership path in the authenticated Experience.
