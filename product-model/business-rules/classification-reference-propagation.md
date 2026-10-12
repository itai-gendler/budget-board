---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account-type",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "account-type",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "account-type",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "asset-type",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "asset-type",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "asset-type",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "category",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "category",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "category",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "asset",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "budget",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "budget",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "rule-action",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "user-settings",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionCategoryService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AccountTypeService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/AssetTypeService.cs"
    }
  ]
}
---

# Vocabulary changes propagate through their actual financial references

Effective-vocabulary conflicts, parent validation, rename/removal propagation and built-in-switch effects follow actual references. Recurring references are not assumed repaired.
