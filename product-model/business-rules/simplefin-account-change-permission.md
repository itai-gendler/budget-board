---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-account",
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
      "target": "server/BudgetBoard.Service/SimpleFinAccountService.cs"
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

# Only the owning User or the admitted unattended processing changes SimpleFIN account

The owning User may change SimpleFIN account through the declared ownership path in the authenticated Experience. Scheduled synchronization may also change it only while Automatic sync disabled is false.
