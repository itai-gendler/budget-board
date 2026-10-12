---
{
  "kind": "validation",
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
      "text": "Missing settings or no eligible training data reports failure without producing a replacement classifier.",
      "kind": "condition",
      "entities": [],
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

# Train auto categorizer no training data

## Trigger

The User chooses a training range and requests classifier training.

## Outcome

Missing settings or no eligible training data reports failure without producing a replacement classifier.
