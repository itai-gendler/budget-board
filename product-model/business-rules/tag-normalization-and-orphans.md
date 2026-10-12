---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tag",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "tag",
      "effect": "reads"
    },
    {
      "type": "entity",
      "id": "tag",
      "effect": "removes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TagService.cs"
    }
  ]
}
---

# Tags normalize spelling and disappear when orphaned

Trim/case-normalize, reuse normalized matches, reject empty/over-fifty-character values and overlapping requests, clean orphaned Tags.
