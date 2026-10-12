---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transaction-import",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "transaction-import",
      "effect": "changes"
    },
    {
      "type": "entity",
      "id": "transaction",
      "effect": "creates"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionImportService.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/helpers/transactionImport.ts"
    }
  ]
}
---

# Import failures retain committed rows and stable replay identities

Hundred-row batches, row retry after batch failure, retained committed rows and stable identities. Counters need not equal unique new records.
