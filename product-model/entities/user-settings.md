---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/UserSettingsService.cs"
    }
  ],
  "relations": [
    {
      "entity": "auto-categorizer",
      "verb": "contains",
      "cardinality": "one-to-one"
    }
  ]
}
---

# User settings

Lazily initialized, then changed by section settings.

## Information kept

- **Currency** — Display currency selection.
- **Decimal places** — Selected precision, zero through three.
- **Language** — Shipped locale or system-default choice.
- **Date format** — Supported date-display selection.
- **Budget warning threshold** — Warning percentage, zero through one hundred.
- **Force-sync lookback months** — Selected history lookback, zero through twelve.
- **Built-in account types disabled** — Whether the built-in Account-type vocabulary is disabled.
- **Built-in asset types disabled** — Whether the built-in Asset-type vocabulary is disabled.
- **Built-in categories disabled** — Whether the built-in transaction-category vocabulary is disabled.
- **Auto categorizer enabled** — Whether new-record processing may consult the trained classifier.
- **Minimum probability percentage** — Prediction acceptance threshold, zero through one hundred.
