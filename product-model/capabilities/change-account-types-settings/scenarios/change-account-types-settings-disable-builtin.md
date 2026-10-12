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
      "text": "The Product disables the built-in vocabulary in User settings, clears dependent selections and unparents custom Account type entries referencing the disabled vocabulary.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Built-in account types disabled"
          ]
        },
        {
          "entity": "account-type",
          "effect": "changes",
          "facts": [
            "Parent"
          ]
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

# Change account types settings disable builtin

## Trigger

The User changes the built-in type availability setting.

## Outcome

The Product disables the built-in vocabulary in User settings, clears dependent selections and unparents custom Account type entries referencing the disabled vocabulary.
