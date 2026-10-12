---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a type name, optional parent and Classification.",
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
      "text": "The Product creates Account type after effective-name and parent validation; Classification follows the supplied valid parent when applicable.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-type",
          "effect": "creates",
          "facts": [
            "Name",
            "Parent",
            "Classification"
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

# Add account type add

## Trigger

The User submits a type name, optional parent and asset/liability classification.

## Outcome

The Product creates Account type after effective-name and parent validation; Classification follows the supplied valid parent when applicable.
