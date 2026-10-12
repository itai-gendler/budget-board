---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to name, parent or income/expense/transfer classification.",
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
      "text": "The Product changes Category Name, Parent and Classification; matching Transaction classifications, Budget category names, child parents and Rule action input follow the rename. Recurring definitions are not universally repaired.",
      "kind": "product",
      "entities": [
        {
          "entity": "category",
          "effect": "changes",
          "facts": [
            "Name",
            "Parent",
            "Classification"
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
          "effect": "changes",
          "facts": [
            "Category"
          ]
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

# Edit category rename and change type

## Trigger

The User submits changes to name, parent or income/expense/transfer classification.

## Outcome

The Product changes Category Name, Parent and Classification; matching Transaction classifications, Budget category names, child parents and Rule action values follow the rename. Recurring definitions are not universally repaired.
