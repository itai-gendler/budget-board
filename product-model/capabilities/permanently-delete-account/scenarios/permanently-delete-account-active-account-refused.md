---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms permanent removal of the selected deleted record and its history.",
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
      "text": "Permanent removal of an active record is refused; soft deletion must precede it.",
      "kind": "condition",
      "entities": [],
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

# Permanently delete account active account refused

## Trigger

The User confirms permanent removal of the selected deleted record and its history.

## Outcome

Permanent removal of an active record is refused; soft deletion must precede it.
