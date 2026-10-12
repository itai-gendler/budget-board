---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the built-in type availability setting.",
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
      "text": "The Product reenables the built-in vocabulary through User settings after checking custom-name conflicts.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Built-in account types disabled"
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

# Change account types settings enable builtin

## Trigger

The User changes the built-in type availability setting.

## Outcome

The Product reenables the built-in vocabulary through User settings after checking custom-name conflicts.
