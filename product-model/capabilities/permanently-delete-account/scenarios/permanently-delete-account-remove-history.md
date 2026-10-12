---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms permanent removal of the selected deleted record and its history.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-accounts"
        }
      }
    },
    {
      "text": "The Product removes the already deleted Account, its Balance and Transaction history and account-related Recurring transaction definitions. Goal.Selected accounts loses the removed membership without rebasing Initial amount.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "removes",
          "from": "Deleted"
        },
        {
          "entity": "balance",
          "effect": "removes",
          "with": "account"
        },
        {
          "entity": "transaction",
          "effect": "removes",
          "with": "account",
          "from": "Active",
          "as": "active-history"
        },
        {
          "entity": "recurring-transaction",
          "effect": "removes",
          "with": "account"
        },
        {
          "entity": "goal",
          "effect": "changes",
          "facts": [
            "Selected accounts"
          ]
        },
        {
          "entity": "transaction",
          "effect": "removes",
          "as": "deleted-history",
          "with": "account",
          "from": "Deleted"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-accounts"
        }
      }
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

# Permanently delete account remove history

## Trigger

The User confirms permanent removal of the selected deleted record and its history.

## Outcome

The Product removes the already deleted Account, its Balance and Transaction history and account-related Recurring transaction definitions. Goal.Selected accounts loses the removed membership without rebasing Initial amount.

## Edge cases

- A structural demo-filter refusal preserves retained financial history.
