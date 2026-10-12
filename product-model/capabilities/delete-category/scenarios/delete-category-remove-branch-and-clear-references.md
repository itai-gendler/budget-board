---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of the selected classification branch.",
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
      "text": "The Product removes the Category branch, clears matching Transaction category/subcategory facts, removes corresponding Budget records and clears matching Rule action category input.",
      "kind": "product",
      "entities": [
        {
          "entity": "category",
          "effect": "removes"
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

# Delete category remove branch and clear references

## Trigger

The User confirms removal of the selected classification branch.

## Outcome

The Product removes the Category branch, clears matching Transaction category/subcategory facts, removes corresponding Budget records and clears matching Rule action category values.
