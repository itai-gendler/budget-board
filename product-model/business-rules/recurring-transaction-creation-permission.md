---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "recurring-transaction",
      "effect": "creates",
      "contexts": [
        {
          "place": "web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/RecurringRuleService.cs"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "owns",
          "entity": "user"
        }
      ]
    }
  ]
}
---

# Only the owning User creates Recurring transaction

The owning User may create Recurring transaction through the declared ownership path in the authenticated Experience.
