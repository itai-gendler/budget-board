---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User chooses the Net worth summary and submits Add.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "The Product creates Net-worth widget containing default Net-worth group, Net-worth line and Net-worth category sources for Spending, Credit Cards, Loans, Savings, Liquid, Investments, property and Total.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-widget",
          "effect": "creates",
          "facts": [
            "Groups"
          ]
        },
        {
          "entity": "net-worth-group",
          "effect": "creates",
          "facts": [
            "Order",
            "Lines"
          ],
          "with": "net-worth-widget"
        },
        {
          "entity": "net-worth-line",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ],
          "with": "net-worth-group"
        },
        {
          "entity": "net-worth-category",
          "effect": "creates",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
          ],
          "with": "net-worth-line"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    }
  ]
}
---

# Add widget net worth

## Trigger

The User chooses the Net worth summary and submits Add.

## Outcome

The Product creates Net-worth widget containing default Net-worth group, Net-worth line and Net-worth category sources for Spending, Credit Cards, Loans, Savings, Liquid, Investments, Assets and Total.
