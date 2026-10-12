---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "simplefin-account",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "simplefin-account",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "lunchflow-account",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SimpleFinService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/LunchFlowService.cs"
    }
  ]
}
---

# Provider history and snapshot handling retain their differing date scopes

Existing provider references, including deleted rows, prevent reimport. SimpleFIN pending/posted timestamp handling and deleted-Account skip differ from LunchFlow. LunchFlow local balance snapshots use the current local date. No conversion; Pending is not retained.
