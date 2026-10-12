---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-organization",
      "effect": "changes",
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
      "target": "server/BudgetBoard.Service/SimpleFinOrganizationService.cs"
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

# Only the owning User or the admitted unattended processing changes SimpleFIN organization

The owning User may change SimpleFIN organization through the declared ownership path in the authenticated Experience. Scheduled synchronization may also change it only while Automatic sync disabled is false.
