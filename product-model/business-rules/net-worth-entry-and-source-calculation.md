---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "net-worth-widget",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "net-worth-group",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "net-worth-group",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "net-worth-group",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "net-worth-group",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "net-worth-line",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "net-worth-line",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "net-worth-line",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "net-worth-line",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "net-worth-category",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "net-worth-category",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "net-worth-category",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "net-worth-category",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "asset",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "balance",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "value",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/widgets.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs"
    }
  ]
}
---

# Net-worth sources retain ordered entries and name-based recursive calculation

Ordered entries; empty-group cleanup; Account-type, Asset-all/type and recursive line-name sources may overlap. Browser lowercase cycle filtering differs from exact-case server `Line`/`Name` checks. Renames do not maintain references; reorder payloads replace supplied lists. Default groups contain Spending, Credit Cards, Loans and Savings; Liquid combines those lines alongside Investments and Assets, and Total combines Liquid, Investments and Assets. Account sources sum visible latest balances by effective type; Asset sources sum visible latest values for all or one type. Name-based line sources recursively sum matching lines and can overlap. Removing lines also removes empty groups. Reordering replaces supplied lists rather than universally retaining omitted entries.
