---
{
  "kind": "validation",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User attempts to remove the final comparison entry.",
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
      "text": "The browser does not offer removal of the final entry. An empty submitted server list preserves the existing list rather than proving a server rejection.",
      "kind": "condition",
      "entities": [],
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

# Remove rule condition last entry control unavailable

## Trigger

The User attempts to remove the final comparison entry.

## Outcome

The browser does not offer removal of the final entry. An empty submitted server list preserves the existing list rather than proving a server rejection.
