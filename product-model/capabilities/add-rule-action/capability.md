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

# Add rule action

Add an action entry by saving a nonempty replacement action list; action definitions are validated before replacement.
