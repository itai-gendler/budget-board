---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SimpleFinAccountService.cs"
    }
  ],
  "relations": [
    {
      "entity": "account",
      "verb": "links",
      "cardinality": "one-to-one"
    }
  ]
}
---

# SimpleFIN account

Discovered/refreshed, linked/unlinked and removed.

## Information kept

- **Provider reference** — Provider record reference used for matching and duplicate avoidance.
- **Name** — Name used to present or select this instance.
- **Currency** — Currency reported by SimpleFIN; monetary amounts are used without conversion.
- **Reported balance** — Most recently reported monetary balance.
- **Balance date** — Reported provider balance date.
- **Sync start** — Selected beginning of provider history retrieval.
- **Last sync** — Most recent recorded synchronization time.
- **Local account link** — Associated local Account, when linked.
