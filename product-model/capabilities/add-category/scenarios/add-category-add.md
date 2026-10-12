---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits a classification name, optional parent and income/expense/transfer classification.",
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
      "text": "The Product creates Category after effective-name and parent validation; Classification follows the supplied valid parent when applicable.",
      "kind": "product",
      "entities": [
        {
          "entity": "category",
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

# Add category add

## Trigger

The User submits a classification name, optional parent and income/expense/transfer classification.

## Outcome

The Product creates Category after effective-name and parent validation; Classification follows the supplied valid parent when applicable.
