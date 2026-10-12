---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "auto-categorizer",
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
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "user-settings"
        },
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

# Only the owning User or the admitted unattended processing reads Auto categorizer

The owning User may read Auto categorizer through the declared ownership path in the authenticated Experience. The inspected import worker or shared automatic financial processing may also read it; disabling scheduled synchronization does not disable this grant.
