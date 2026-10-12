---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction",
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

# Only the owning User or the admitted unattended processing changes Transaction

The owning User may change Transaction through the declared ownership path in the authenticated Experience. The inspected import worker or shared automatic financial processing may also change it; disabling scheduled synchronization does not disable this grant.
