---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens recurring definitions, assignments and projected occurrences.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
    },
    {
      "text": "The Product presents Recurring transaction definitions, assigned Transaction records, configured or median estimated amounts and unmatched projected occurrences. Projections do not create financial activity entries.",
      "kind": "product",
      "entities": [
        {
          "entity": "recurring-transaction",
          "effect": "reads",
          "facts": [
            "Merchant",
            "Category",
            "Subcategory",
            "Cadence",
            "Start date",
            "End date",
            "Active",
            "Amount mode",
            "Amount"
          ]
        },
        {
          "entity": "transaction",
          "effect": "reads",
          "facts": [
            "Date",
            "Merchant",
            "Amount",
            "Category",
            "Subcategory",
            "Notes",
            "Source",
            "Provider reference",
            "Deletion date",
            "Tags",
            "Recurring assignment",
            "Transfer counterpart"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::recurring-transactions"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/RecurringRuleService.cs"
    }
  ]
}
---

# Browse recurring transactions rules and projections

## Trigger

The User opens recurring definitions, assignments and projected occurrences.

## Outcome

The Product presents Recurring transaction definitions, assigned Transaction records, configured or median estimated amounts and unmatched projected occurrences. Projections do not create ledger records.
