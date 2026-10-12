---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "category",
      "effect": "reads",
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
      "target": "server/BudgetBoard.Service/TransactionCategoryService.cs"
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
    },
    {
      "unattended": true
    }
  ]
}
---

# Only the owning User or the admitted unattended processing reads Category

The owning User may read Category through the declared ownership path in the authenticated Experience. The inspected import worker or shared automatic financial processing may also read it; disabling scheduled synchronization does not disable this grant.
