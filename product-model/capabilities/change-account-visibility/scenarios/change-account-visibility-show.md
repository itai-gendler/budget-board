---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the selected record’s visibility setting.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
        }
      }
    },
    {
      "text": "The Product sets Account.Account hidden to false. The associated summaries follow their own visibility eligibility.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Account hidden"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::accounts"
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

# Change account visibility show

## Trigger

The User changes the selected record’s Hide Account setting.

## Outcome

The Product sets Account.Account hidden to false. The associated summaries follow their own visibility eligibility.
