---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses a training range and requests classifier training.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::auto-categorizer"
        }
      }
    },
    {
      "text": "The Product trains Auto categorizer using categorized nondeleted merchant-bearing Transaction records on nondeleted Accounts within the selected range, replaces Trained classifier and retains Training date and actual range. Prediction quality is not guaranteed.",
      "kind": "product",
      "entities": [
        {
          "entity": "auto-categorizer",
          "effect": "changes",
          "facts": [
            "Trained classifier",
            "Training date",
            "Training start",
            "Training end"
          ],
          "from": "Untrained",
          "to": "Trained"
        },
        {
          "entity": "transaction",
          "effect": "reads",
          "facts": [
            "Date",
            "Merchant",
            "Category",
            "Subcategory",
            "Deletion date"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Deletion date"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::auto-categorizer"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    }
  ]
}
---

# Train auto categorizer replace model

## Trigger

The User chooses a training range and requests classifier training.

## Outcome

The Product trains Auto categorizer using categorized nondeleted merchant-bearing Transaction records on nondeleted Accounts within the selected range, replaces Trained classifier and retains Training date and actual range. Prediction quality is not guaranteed.

## Edge cases

- Retraining an already trained classifier replaces its retained model and metadata.
