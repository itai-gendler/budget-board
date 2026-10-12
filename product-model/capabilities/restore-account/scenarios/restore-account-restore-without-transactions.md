---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses Restore for the selected deleted record.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-accounts"
        }
      }
    },
    {
      "text": "The Product clears Account and Institution deletion markers. Deleted Transaction history stays deleted, and former financial type and provider links are not restored.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Deletion date"
          ],
          "from": "Deleted",
          "to": "Active"
        },
        {
          "entity": "institution",
          "effect": "changes",
          "facts": [
            "Deletion date"
          ],
          "from": "Deleted",
          "to": "Active"
        },
        {
          "entity": "transaction",
          "effect": "reads",
          "facts": [
            "Deletion date"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::deleted-accounts"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountService.cs"
    }
  ]
}
---

# Restore account restore without transactions

## Trigger

The User chooses Restore for the selected deleted record.

## Outcome

The Product clears Account and Institution deletion markers. Deleted Transaction history stays deleted, and former account type and provider links are not restored.

## Edge cases

- A structural demo-filter refusal preserves the deleted record.
