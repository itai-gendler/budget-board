---
{
  "entities": [
    {
      "entity": "budget",
      "shows": [
        "Category",
        "Month"
      ]
    },
    {
      "entity": "transaction",
      "shows": [
        "Date",
        "Merchant",
        "Amount",
        "Category",
        "Subcategory",
        "Notes",
        "Tags",
        "Recurring assignment",
        "Transfer counterpart"
      ],
      "collects": [
        "Date",
        "Merchant",
        "Amount",
        "Category",
        "Subcategory",
        "Notes",
        "Tags",
        "Recurring assignment",
        "Transfer counterpart"
      ]
    },
    {
      "entity": "recurring-transaction",
      "shows": [
        "Merchant",
        "Category",
        "Subcategory",
        "Cadence",
        "Start date",
        "End date",
        "Active",
        "Amount mode",
        "Amount"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Budgets/BudgetsContent/BudgetDetails/BudgetDetails.tsx"
    }
  ]
}
---

# Budget details

Selected category/month analysis, recent Transactions and recurring projections. Shows category/month and relevant Transaction facts. Collects transaction edits through bulk selection. Budget-limit and rollover edits use the Budgets context.
