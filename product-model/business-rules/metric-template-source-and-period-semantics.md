---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "metric-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "metric-widget",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "metric-widget",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "budget",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "goal",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/metricWidget.ts#resolveTemplate"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/metricWidget.ts#resolveMetricPeriod"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/metricWidget.ts#buildDataRequirements"
    }
  ]
}
---

# Metric templates use source-specific formulas and period requirements

Literal/template evaluation and source-specific formulas. Named/calendar periods, unsupported/error markers, Budget remaining clamped without rollover, all-time Budget query behavior, interest-excluded Goal responses and currency-template privacy masking remain explicit. Sources are transactions.sum/count/avg, budgets.total/spent/remaining/percent_used, goals.percent_complete/current_amount/target/monthly_contribution and accounts.balance. Transaction sum/average use absolute signed net aggregates; expense includes nonincome types unless otherwise filtered. Budget metrics require category, ignore rollover, clamp remaining to zero and use absolute net spending; all-time Budget queries return no months. Goal metrics use the first case-insensitive name and responses without interest. Account balance uses type with child types or the first matching name and ignores period. Periods include this/last month, this year, last N weeks/months/years, all time and supported calendar offsets; custom inclusive endpoints are supported only for Transaction metrics. Unknown metrics return zero; unknown sources, invalid periods and caught failures produce markers. Currency expressions mask the whole rendered value/label under privacy selection; Title remains literal.
