---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "balance",
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

# Only the owning User or the admitted unattended processing creates Balance

The owning User may create Balance through the declared ownership path in the authenticated Experience. The inspected import worker or shared automatic financial processing may also create it; disabling scheduled synchronization does not disable this grant.
