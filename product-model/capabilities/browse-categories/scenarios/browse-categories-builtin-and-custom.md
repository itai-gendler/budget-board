---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the effective classification vocabulary and its built-in availability setting.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::categories"
        }
      }
    },
    {
      "text": "The Product presents the effective built-in vocabulary and custom Category facts, respecting User settings built-in availability.",
      "kind": "product",
      "entities": [
        {
          "entity": "category",
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
            "Built-in categories disabled"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::categories"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionCategoryService.cs"
    }
  ]
}
---

# Browse categories builtin and custom

## Trigger

The User opens the effective classification vocabulary and its built-in availability setting.

## Outcome

The Product presents the effective built-in vocabulary and custom Category facts, respecting User settings built-in availability.
