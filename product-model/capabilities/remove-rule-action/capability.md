---
{
  "availability": [
    {
      "place": "web::authenticated"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AutomaticRuleService.cs"
    }
  ],
  "domain": "automatic-rules"
}
---

# Remove rule action

Remove an action entry by saving a remaining nonempty replacement list; the browser prevents final-entry removal and an empty server list retains current entries.
