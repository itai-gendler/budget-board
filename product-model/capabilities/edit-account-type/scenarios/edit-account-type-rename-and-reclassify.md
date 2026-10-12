---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User submits changes to the selected type’s name, parent or Classification.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-types"
        }
      }
    },
    {
      "text": "The Product changes Account type Name, Parent and Classification, with matching Account type selections and child parent/classification propagation.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-type",
          "effect": "changes",
          "facts": [
            "Name",
            "Parent",
            "Classification"
          ]
        },
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Type"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::account-types"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    }
  ]
}
---

# Edit account type rename and reclassify

## Trigger

The User submits changes to the selected type’s name, parent or asset/liability classification.

## Outcome

The Product changes Account type Name, Parent and Classification, with matching Account type selections and child parent/classification propagation.
