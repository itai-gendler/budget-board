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
      "target": "server/BudgetBoard.Service/AssetTypeService.cs"
    }
  ],
  "domain": "asset-types"
}
---

# Change asset types settings

Disable or reenable built-in Asset types; disabling clears corresponding references and parents, while reenable refuses custom-name conflicts.
