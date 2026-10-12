---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "category",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "account-type",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "asset",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "asset-type",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "value",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/charts.ts#buildFlowsChartData"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/components/Charts/ValueChart/helpers/valueChart.ts#buildValueChartData"
    }
  ]
}
---

# Analysis modes retain source scopes and signed aggregation

Eight modes retain scopes. Flows net signed leaves, skip net-zero groups and derive surplus/deficit. Cash available is a chart bridge. Account net worth sums signed balances; dated charts carry snapshots and use zero before the first represented value. Spending comparisons stop the current month at today; other months use their complete period. Flows aggregate signed leaf amounts, classify their net sign, omit net-zero groups, retain nonzero Transfer net amounts and bridge income/spending through Cash available. Tooltips use one-decimal percentages. Account net worth includes Accounts rather than Asset entities; snapshot charts carry represented preceding values and use zero before the first represented value.
