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

# Add automatic rule

Save nonempty condition and action lists as an Automatic rule; validate actions before creation and retain matching conditions for execution.
