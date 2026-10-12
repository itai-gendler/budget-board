---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User requests the shipped default net-worth configuration for the selected summary.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::widget-settings"
        }
      }
    },
    {
      "text": "The Product replaces Net-worth widget.Groups, removing old Net-worth group, Net-worth line and Net-worth category entries and restoring shipped default sources.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-widget",
          "effect": "changes",
          "facts": [
            "Groups"
          ]
        },
        {
          "entity": "net-worth-group",
          "effect": "removes",
          "as": "old-groups"
        },
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "as": "old-lines",
          "with": "old-groups"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
          "as": "old-sources",
          "with": "old-lines"
        },
        {
          "entity": "net-worth-group",
          "effect": "creates",
          "facts": [
            "Order",
            "Lines"
          ],
          "as": "new-groups"
        },
        {
          "entity": "net-worth-line",
          "effect": "creates",
          "facts": [
            "Name",
            "Order",
            "Categories"
          ],
          "as": "new-lines",
          "with": "new-groups"
        },
        {
          "entity": "net-worth-category",
          "effect": "creates",
          "facts": [
            "Source type",
            "Selection method",
            "Selection value"
          ],
          "as": "new-sources",
          "with": "new-lines"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::widget-settings"
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

# Reset net worth widget restore default groups

## Trigger

The User requests the shipped default net-worth configuration for the selected summary.

## Outcome

The Product replaces Net-worth widget.Groups, removing old Net-worth group, Net-worth line and Net-worth category entries and restoring shipped default sources.
