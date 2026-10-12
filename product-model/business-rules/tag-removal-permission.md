---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tag",
      "effect": "removes",
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
      "target": "server/BudgetBoard.Service/TagService.cs"
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

# Only the owning User or scheduled synchronization removes Tag

The owning User may remove Tag through the declared ownership path in the authenticated Experience. Scheduled synchronization may also remove it only while Automatic sync disabled is false.
