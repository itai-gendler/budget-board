---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/RecurringRuleService.cs"
    }
  ],
  "relations": [
    {
      "entity": "transaction",
      "verb": "matches",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "recurring-transactions"
}
---

# Recurring transaction

Created, edited and removed. Active is editable configuration. Forecast occurrences are projections.

## Information kept

- **Merchant** — Description or recurring merchant criterion.
- **Category** — Parent transaction-category name.
- **Subcategory** — Leaf transaction-category name.
- **Cadence** — Version-one interval or per-unit calendar schedule.
- **Start date** — Inclusive schedule beginning.
- **End date** — Optional inclusive schedule ending.
- **Active** — Whether the recurring definition is active.
- **Amount mode** — Configured or automatically estimated amount selection.
- **Amount** — Signed monetary amount.
