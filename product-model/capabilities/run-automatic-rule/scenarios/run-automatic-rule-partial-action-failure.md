---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User runs ordered actions whose later operation fails after an earlier successful operation.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::automatic-rules"
        }
      }
    },
    {
      "text": "A later Rule action fails after earlier operations; the Product keeps earlier Transaction, Balance and Tag effects, logs the caught action failure and continues the ordered run. The summary reports successful action updates. Manual-source date-changing actions can create a missing dated Balance.",
      "kind": "product",
      "entities": [
        {
          "entity": "automatic-rule",
          "effect": "reads",
          "facts": [
            "Conditions",
            "Actions"
          ]
        },
        {
          "entity": "rule-condition",
          "effect": "reads",
          "facts": [
            "Field",
            "Operator",
            "Comparison value"
          ]
        },
        {
          "entity": "rule-action",
          "effect": "reads",
          "facts": [
            "Field",
            "Operator",
            "Action value"
          ]
        },
        {
          "entity": "transaction",
          "effect": "changes",
          "facts": [
            "Date",
            "Merchant",
            "Amount",
            "Category",
            "Subcategory",
            "Notes",
            "Tags",
            "Transfer counterpart",
            "Deletion date",
            "Recurring assignment"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Source",
            "Transactions hidden"
          ]
        },
        {
          "entity": "balance",
          "effect": "changes",
          "facts": [
            "Amount"
          ],
          "as": "existing-balances"
        },
        {
          "entity": "tag",
          "effect": "creates",
          "facts": [
            "Display value",
            "Normalized value"
          ],
          "as": "added-tags"
        },
        {
          "entity": "tag",
          "effect": "removes",
          "as": "orphan-tags"
        },
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
          "entity": "balance",
          "effect": "creates",
          "facts": [
            "Date",
            "Amount"
          ],
          "as": "missing-dated-balance"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::automatic-rules"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    }
  ]
}
---

# Run automatic rule partial action failure

## Trigger

The User runs ordered actions whose later operation fails after an earlier successful operation.

## Outcome

A later Rule action fails after earlier operations; the Product keeps earlier Transaction, Balance and Tag effects, logs the caught action failure and continues the ordered run. The summary reports successful action updates.
