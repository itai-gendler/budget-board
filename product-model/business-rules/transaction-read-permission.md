---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction",
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
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "account"
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

# Only the owning User or the admitted unattended processing reads Transaction

The owning User may read Transaction through the declared ownership path in the authenticated Experience. The inspected import worker or shared automatic financial processing may also read it; disabling scheduled synchronization does not disable this grant.
