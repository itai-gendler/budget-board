---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "budget",
      "effect": "reads"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/budgets.ts#getRangeRolloverBudgetIds"
    }
  ]
}
---

# Selected ranges count entering category rollover once

Selected limits sum; earliest entering category rollover counted once.
