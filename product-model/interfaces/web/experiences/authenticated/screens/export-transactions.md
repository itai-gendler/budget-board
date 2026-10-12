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
        "Source"
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
      "target": "client/src/app/Authorized/PageContent/Transactions/TransactionsHeader/ExportTransactionsModal/ExportTransactionsModal.tsx"
    }
  ]
}
---

# Export transactions

Filtered export process with temporary field selection and ordering. Shows selected Transaction facts and Account.Name.
