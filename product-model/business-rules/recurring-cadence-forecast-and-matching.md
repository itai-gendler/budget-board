---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "recurring-transaction",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "recurring-transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "recurring-transaction",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/RecurringRuleService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/RecurringRuleOccurrenceCalculator.cs"
    }
  ]
}
---

# Recurring forecasts and matching follow calendar and ambiguity constraints

Version-one interval/per-unit day/week/month/year cadence; positive interval, maxima 1/7/31/366, inclusive bounds and clamping. Unmatched forecasts exclude Transfer/Hide from Budgets and hidden Transactions. Automatic amount is assigned nondeleted-amount median when enough records exist, otherwise configured amount. Matching uses normalized identifiers, 20% amount tolerance and five-day pairing; ambiguity remains unassigned. Automatic amounts use the median of at least two assigned nondeleted amounts, otherwise the configured amount. Pairing uses nearest scheduled dates within five days and leaves ambiguous matches unassigned. Creation matching normalizes alphanumeric Merchant/Category/Subcategory, allows 20% amount tolerance and requires exactly one matching definition. Monthly/yearly dates clamp to available calendar days; per-unit positions spread across the unit and remain distinct. Forecasts never insert ledger records.
