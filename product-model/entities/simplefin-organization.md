---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SimpleFinOrganizationService.cs"
    }
  ],
  "relations": [
    {
      "entity": "simplefin-account",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ]
}
---

# SimpleFIN organization

Discovered/refreshed and removed with provider data.

## Information kept

- **Name** — Name used to present or select this instance.
- **Domain** — Reported organization domain.
- **Provider URL** — Reported service address.
- **Institution URL** — Reported institution address.
- **Provider reference** — Provider record reference used for matching and duplicate avoidance.
