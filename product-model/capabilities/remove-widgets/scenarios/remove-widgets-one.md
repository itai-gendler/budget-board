---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User confirms removal of one selected dashboard summary.",
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
      "text": "The Product removes the selected instance from its configured family; financial records remain.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "For a selected Dashboard widget, the Product removes that instance.",
      "kind": "product",
      "entities": [
        {
          "entity": "dashboard-widget",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "For a selected Accounts widget, the Product removes that instance.",
      "kind": "product",
      "entities": [
        {
          "entity": "accounts-widget",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "For a selected Flows widget, the Product removes that instance.",
      "kind": "product",
      "entities": [
        {
          "entity": "flows-widget",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "For a selected Metric widget, the Product removes that instance.",
      "kind": "product",
      "entities": [
        {
          "entity": "metric-widget",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::dashboard"
        }
      }
    },
    {
      "text": "For a selected Net-worth widget, the Product removes that instance.",
      "kind": "product",
      "entities": [
        {
          "entity": "net-worth-widget",
          "effect": "removes"
        },
        {
          "entity": "net-worth-group",
          "effect": "removes",
          "with": "net-worth-widget"
        },
        {
          "entity": "net-worth-line",
          "effect": "removes",
          "with": "net-worth-group"
        },
        {
          "entity": "net-worth-category",
          "effect": "removes",
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

# Remove widgets one

## Trigger

The User confirms removal of one selected dashboard summary.

## Outcome

The Product removes the selected type instance from the appropriate Dashboard widget, Accounts widget, Flows widget, Metric widget or Net-worth widget family. Removing net-worth configuration removes contained Net-worth group, Net-worth line and Net-worth category entries. Financial records remain.

## Decision points

### Selected configuration family

Which family contains the selected widget?

- Dashboard widget → remove that family’s selected instance; the collection loses one widget.
- Accounts widget → remove that family’s selected instance; the collection loses one widget.
- Flows widget → remove that family’s selected instance; the collection loses one widget.
- Metric widget → remove that family’s selected instance; the collection loses one widget.
- Net-worth widget → remove that family’s selected instance; the collection loses one widget.
