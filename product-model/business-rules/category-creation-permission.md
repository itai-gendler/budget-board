---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "category",
      "effect": "creates",
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
    }
  ]
}
---

# Only the owning User creates Category

The owning User may create Category through the declared ownership path in the authenticated Experience.
