---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/LunchFlowAccountService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/LunchFlowService.cs"
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

# LunchFlow account

Discovered/refreshed, linked/unlinked and removed.

## Information kept

- **Provider reference** — Provider record reference used for matching and duplicate avoidance.
- **Name** — Name used to present or select this instance.
- **Institution name** — Institution name reported by the provider.
- **Provider** — Reported provider description.
- **Status** — Connection/import status reported by LunchFlow.
- **Currency** — Currency reported by LunchFlow; monetary amounts are used without conversion.
- **Reported balance** — Most recently reported monetary balance.
- **Balance date** — Application UTC timestamp recorded when LunchFlow balance data is retrieved, rather than a provider-reported effective date.
- **Sync start** — Selected beginning of provider history retrieval.
- **Last sync** — Most recent recorded synchronization time.
- **Local account link** — Associated local Account, when linked.
