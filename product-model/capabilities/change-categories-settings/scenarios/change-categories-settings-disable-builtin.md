---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the built-in classification availability setting.",
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
      "text": "The Product disables the built-in vocabulary in User settings, clears dependent selections and unparents custom Category entries referencing the disabled vocabulary.",
      "kind": "product",
      "entities": [
        {
          "entity": "user-settings",
          "effect": "changes",
          "facts": [
            "Built-in categories disabled"
          ]
        },
        {
          "entity": "category",
          "effect": "changes",
          "facts": [
            "Parent"
          ]
        },
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Category",
            "Subcategory"
          ]
        },
        {
          "entity": "budget",
          "effect": "removes"
        },
        {
          "entity": "rule-action",
          "effect": "changes",
          "facts": [
            "Action value"
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

# Change categories settings disable builtin

## Trigger

The User changes the built-in classification availability setting.

## Outcome

The Product disables the built-in vocabulary in User settings, clears dependent selections and unparents custom Category entries referencing the disabled vocabulary.
