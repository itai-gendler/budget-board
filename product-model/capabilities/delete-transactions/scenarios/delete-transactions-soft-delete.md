---
{
  "kind": "primary",
  "routes": {
    "transactions": "Transactions",
    "transaction-details": "Transaction details",
    "dashboard": "Dashboard",
    "budget-details": "Budget details"
  },
  "steps": [
    {
      "text": "The User confirms deletion of the selected financial activity entries.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "transactions": {
          "place": "web::authenticated::transactions"
        },
        "transaction-details": {
          "place": "web::authenticated::transaction-details"
        },
        "dashboard": {
          "place": "web::authenticated::dashboard"
        },
        "budget-details": {
          "place": "web::authenticated::budget-details"
        }
      }
    },
    {
      "text": "The Product marks selected Transaction records deleted and clears classification, Subcategory, Tags and Transfer counterpart. Manual Account sources reverse the contribution in Balance snapshots; orphan Tag records are removed. A linked Transaction counterpart is detached.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Deletion date",
            "Category",
            "Subcategory",
            "Tags",
            "Transfer counterpart"
          ],
          "as": "selected",
          "from": "Active",
          "to": "Deleted"
        },
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Transfer counterpart"
          ],
          "as": "counterpart"
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Source"
          ]
        },
        {
          "entity": "balance",
          "effect": "changes",
          "facts": [
            "Amount"
          ]
        },
        {
          "entity": "tag",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "transactions": {
          "place": "web::authenticated::transactions"
        },
        "transaction-details": {
          "place": "web::authenticated::transaction-details"
        },
        "dashboard": {
          "place": "web::authenticated::dashboard"
        },
        "budget-details": {
          "place": "web::authenticated::budget-details"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionService.cs"
    }
  ]
}
---

# Delete transactions soft delete

## Trigger

The User confirms deletion of the selected financial activity entries.

## Outcome

The Product marks selected Transaction records deleted and clears Category, Subcategory, Tags and Transfer counterpart. Manual Account sources reverse the contribution in Balance snapshots; orphan Tag records are removed. A linked Transaction counterpart is detached.

## Edge cases

- Repeated deletion can repeat the balance adjustment; a general idempotence guarantee is not established.
