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
      "target": "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs"
    }
  ],
  "domain": "auto-categorizer"
}
---

# Change auto categorizer settings

Set classifier activation and a minimum accepted probability from zero through one hundred; activation requires a retained model.
