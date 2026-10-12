---
{
  "kind": "validation",
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
      "text": "Reenabling a built-in vocabulary with conflicting custom names is refused; the selected setting remains.",
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

# Change categories settings custom name conflict

## Trigger

The User changes the built-in classification availability setting.

## Outcome

Reenabling a built-in vocabulary with conflicting custom names is refused; the selected setting remains.
