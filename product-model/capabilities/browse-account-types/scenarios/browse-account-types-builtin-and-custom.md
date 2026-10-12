---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the effective type vocabulary and its built-in availability setting.",
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
      "text": "The Product presents the effective built-in vocabulary and custom Account type facts, respecting User settings built-in availability.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-type",
          "effect": "reads",
          "facts": [
            "Name",
            "Parent",
            "Classification"
          ]
        },
        {
          "entity": "user-settings",
          "effect": "reads",
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

# Browse account types builtin and custom

## Trigger

The User opens the effective type vocabulary and its built-in availability setting.

## Outcome

The Product presents the effective built-in vocabulary and custom Account type facts, respecting User settings built-in availability.
