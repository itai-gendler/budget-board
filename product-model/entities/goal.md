---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/GoalService.cs#GoalService"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Database/Data/UserDataContext.cs#OnModelCreating"
    }
  ],
  "relations": [
    {
      "entity": "account",
      "verb": "uses",
      "cardinality": "many-to-many"
    }
  ],
  "domain": "goals"
}
---

# Goal

Active, Completed. Planning edits, manual/sync completion and removal are established; reopening is not.

## Information kept

- **Name** — Name used to present or select this instance.
- **Target** — Stored financial target.
- **Initial amount** — Baseline retained at creation.
- **Selected accounts** — Accounts linked at creation and used for balances and monthly progress; planning edits retain this membership.
- **Stored contribution** — Supplied monthly planning contribution, when chosen.
- **Stored target date** — Supplied target date, when chosen.
- **Completed date** — Retained completion date.

## States

### Active

No completion date is recorded.

### Completed

Completion is recorded.
