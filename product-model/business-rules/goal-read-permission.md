---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "goal",
      "effect": "reads",
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
      "target": "server/BudgetBoard.Service/GoalService.cs"
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
    },
    {
      "unattended": true,
      "when": [
        {
          "entity": "deployment-settings",
          "fact": "Automatic sync disabled",
          "is": false
        }
      ]
    }
  ]
}
---

# Only the owning User or the admitted unattended processing reads Goal

The owning User may read Goal through the declared ownership path in the authenticated Experience. Scheduled synchronization may also read it only while Automatic sync disabled is false.
