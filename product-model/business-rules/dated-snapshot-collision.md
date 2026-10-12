---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "balance",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "balance",
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
      "target": "server/BudgetBoard.Service/BalanceService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/ValueService.cs"
    }
  ]
}
---

# Adding overwrites a same-date snapshot while edit collisions are refused

Addition overwrites same-date Amount; editing into another record’s date is refused.
