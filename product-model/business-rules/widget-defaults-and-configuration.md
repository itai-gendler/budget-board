---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "dashboard-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "dashboard-widget",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "accounts-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "accounts-widget",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "accounts-widget",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "flows-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "flows-widget",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "flows-widget",
      "effect": "removes"
    },
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
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "removes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/Helpers/WidgetSettingsHelpers.cs"
    }
  ]
}
---

# Widgets retain shipped defaults and type-specific configuration constraints

Six defaults; empty Accounts selection means all visible Accounts; Flows 1–12. Browser single-instance limits for Uncategorized transactions, Spending trends and Flows do not apply to the server creation operation. Defaults are Accounts, Uncategorized transactions, Net worth, Spending trends, Metric and Flows. Flows defaults to one month. Metric defaults to This Month’s Spending, value @transactions.sum(this_month,type=expense), label total expenses. Browser limits Flows, Spending trends and Uncategorized transactions to one instance; server creation does not enforce the same maximum.
