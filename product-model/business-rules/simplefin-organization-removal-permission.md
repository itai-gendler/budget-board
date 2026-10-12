---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-organization",
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
      "target": "server/BudgetBoard.Service/SimpleFinOrganizationService.cs"
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

# Only the owning User removes SimpleFIN organization

The owning User may remove SimpleFIN organization through the declared ownership path in the authenticated Experience.
