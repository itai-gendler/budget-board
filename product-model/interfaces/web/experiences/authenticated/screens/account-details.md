---
{
  "entities": [
    {
      "entity": "account",
      "shows": [
        "Name",
        "Type",
        "Interest rate",
        "Source",
        "Account hidden",
        "Transactions hidden",
        "Order",
        "Deletion date"
      ],
      "collects": [
        "Name",
        "Type",
        "Interest rate"
      ]
    },
    {
      "entity": "balance",
      "shows": [
        "Date",
        "Amount"
      ],
      "collects": [
        "Date",
        "Amount"
      ]
    },
    {
      "entity": "institution",
      "shows": [
        "Name"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BalanceService.cs"
    }
  ]
}
---

# Account details

Selected Account and dated Balances. Shows and collects editable Account facts and Balance.Date/Amount.
