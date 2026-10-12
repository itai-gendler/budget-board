---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "asset",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "asset",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "value",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "value",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetService.cs"
    }
  ]
}
---

# Asset acquisition and disposal facts do not create Account ledger entries

Purchase/sale facts and dated Values do not generate Account Transactions.
