---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "balance",
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
      "target": "server/BudgetBoard.Service/BalanceService.cs"
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

# Only the owning User or the admitted unattended processing changes Balance

The owning User may change Balance through the declared ownership path in the authenticated Experience. The inspected import worker or shared automatic financial processing may also change it; disabling scheduled synchronization does not disable this grant.
