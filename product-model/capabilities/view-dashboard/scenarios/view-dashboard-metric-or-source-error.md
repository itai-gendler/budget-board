---
{
  "kind": "edge",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User opens the configured dashboard summaries.",
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
      "text": "Metric widget renders unknown-source, invalid-period or caught-error markers as appropriate; invalid stored configuration produces the widget’s error outcome. Unknown metric names can return zero.",
      "kind": "product",
      "entities": [
        {
          "entity": "metric-widget",
          "effect": "reads",
          "facts": [
            "Title",
            "Value template",
            "Label template"
          ]
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
      "target": "client/src/helpers/charts.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/metricWidget.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Dashboard/Dashboard.tsx"
    }
  ]
}
---

# View dashboard metric or source error

## Trigger

The User opens the configured dashboard summaries.

## Outcome

Metric widget renders unknown-source, invalid-period or caught-error markers as appropriate; invalid stored configuration produces the widget’s error outcome. Unknown metric names can return zero.
