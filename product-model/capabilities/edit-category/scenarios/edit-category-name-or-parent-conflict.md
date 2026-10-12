---
{
  "kind": "validation",
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
      "text": "Conflicting effective name, invalid parent or invalid classification reports refusal without applying the requested vocabulary edit.",
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

# Edit category name or parent conflict

## Trigger

The User submits changes to name, parent or income/expense/transfer classification.

## Outcome

Conflicting effective name, invalid parent or invalid classification reports refusal without applying the requested vocabulary edit.
