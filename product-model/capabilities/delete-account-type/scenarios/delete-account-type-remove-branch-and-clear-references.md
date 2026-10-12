---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected type branch.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-types"
        }
      }
    },
    {
      "text": "The Product removes the Account type branch and clears matching Account.Type selections.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-type",
          "effect": "removes"
        },
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Type"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-types"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    }
  ]
}
---

# Delete account type remove branch and clear references

## Trigger

The User confirms removal of the selected type branch.

## Outcome

The Product removes the Account type branch and clears matching Account.Type selections.
