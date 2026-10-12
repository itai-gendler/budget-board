---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/WidgetSettingsService.cs"
    }
  ],
  "relations": [
    {
      "entity": "account",
      "verb": "selects",
      "cardinality": "many-to-many"
    }
  ],
  "domain": "dashboard"
}
---

# Accounts widget

Created/configured/removed. Empty selection means all otherwise-visible Accounts.

## Information kept

- **Selected accounts** — Configured local record selection; an empty selection displays all otherwise-visible Accounts.
