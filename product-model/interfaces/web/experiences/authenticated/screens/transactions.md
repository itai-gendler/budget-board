---
{
  "entities": [
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
      "entity": "tag",
      "shows": [
        "Display value"
      ],
      "collects": [
        "Display value"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name"
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
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/components/BulkActionBar/BulkActionBar.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    }
  ]
}
---

# Transactions

Transaction collection, selection and bulk operations. Shows and collects Date, Merchant, Amount, Category, Subcategory, Notes and tag membership. Shows source, assignments, transfer counterpart and Account.Name.
