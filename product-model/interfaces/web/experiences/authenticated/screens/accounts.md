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
        "Interest rate",
        "Account hidden",
        "Transactions hidden",
        "Order"
      ]
    },
    {
      "entity": "institution",
      "shows": [
        "Name",
        "Order",
        "Deletion date"
      ],
      "collects": [
        "Name",
        "Order"
      ]
    },
    {
      "entity": "balance",
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
      "target": "server/BudgetBoard.Service/AccountService.cs"
    }
  ]
}
---

# Accounts

Account collection grouped by Institution. Shows and collects names, types, interest, visibility and ordering facts. Shows source, deletion markers and latest Balance results.
