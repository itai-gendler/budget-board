---
{
  "entities": [
    {
      "entity": "transaction",
      "shows": [
        "Date",
        "Amount",
        "Category",
        "Subcategory"
      ]
    },
    {
      "entity": "category",
      "shows": [
        "Name",
        "Parent",
        "Classification"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name"
      ]
    },
    {
      "entity": "balance",
      "shows": [
        "Date",
        "Amount"
      ]
    },
    {
      "entity": "asset",
      "shows": [
        "Name"
      ]
    },
    {
      "entity": "value",
      "shows": [
        "Date",
        "Amount"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/charts.ts"
    }
  ]
}
---

# Trends

One analysis context with eight modes. Shows relevant Transaction, Category, Account, type, Balance, Asset and Value facts.
