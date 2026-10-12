---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    }
  ],
  "domain": "auto-categorizer"
}
---

# Auto categorizer

Untrained, Trained. Initial settings establish untrained configuration; training replaces the classifier.

## Information kept

- **Trained classifier** — Retained model for accepted categorization predictions.
- **Training date** — Training date.
- **Training start** — Beginning of the training data range.
- **Training end** — End of the training data range.

## States

### Untrained

No trained classifier has been established.

### Trained

Training has retained a classifier.
