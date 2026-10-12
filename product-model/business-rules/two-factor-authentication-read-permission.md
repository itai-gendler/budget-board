---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "two-factor-authentication",
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
      "target": "server/BudgetBoard.Service/ApplicationUserService.cs"
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

# Only the owning User reads Two-factor authentication

The owning User may read Two-factor authentication through the declared ownership path in the authenticated Experience.
