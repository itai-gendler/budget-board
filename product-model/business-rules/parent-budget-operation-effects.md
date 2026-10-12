---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "budget",
      "effect": "creates"
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
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#UpdateBudgetAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#DeleteBudgetAsync"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/BudgetService.cs#CreateBudgetsAsync"
    }
  ]
}
---

# Parent allocation effects differ among creation, editing and deletion

Explicit parent creation keeps the entered limit, even below existing child allocations. Creating a missing parent automatically when adding a child sums that month’s child limits. A positive new child increases an existing parent by that child’s limit. Child editing creates or raises the parent to the child-total floor. Parent edits below the child total fail. Deleting a child leaves the parent limit unchanged; deleting the parent removes same-month children. Copy Previous suppresses parent auto-management; its browser action requires one empty selected month.
