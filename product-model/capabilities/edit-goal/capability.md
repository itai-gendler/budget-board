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
      "target": "server/BudgetBoard.Service/GoalService.cs"
    }
  ],
  "domain": "goals"
}
---

# Edit goal

Change a Goal’s name, target or stored schedule while retaining selected Accounts and the creation baseline; partial inputs use their narrower validation.
