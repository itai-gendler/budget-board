---
{
  "kind": "validation",
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
      "text": "An empty or conflicting effective name, invalid parent or invalid classification reports refusal without adding the entry.",
      "kind": "condition",
      "entities": [],
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

# Add category name or parent conflict

## Trigger

The User submits a classification name, optional parent and income/expense/transfer classification.

## Outcome

An empty or conflicting effective name, invalid parent or invalid classification reports refusal without adding the entry.
