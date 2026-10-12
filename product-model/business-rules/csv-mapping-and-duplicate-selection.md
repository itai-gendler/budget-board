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
      "id": "account",
      "effect": "reads"
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

# CSV duplicate review compares mapped incoming rows with existing records

Browser trims/case-normalizes mapped names; server name matching is case-insensitive without the same trim. Default duplicate comparison is date/amount/mapped Account against existing rows. Incoming rows are not generally deduplicated against each other. Duplicate comparison defaults to Date, Amount and mapped Account, with Merchant and Category optional. It compares existing records rather than deduplicating the incoming batch. With no selected fields the browser keeps all rows. The keep-duplicates choice bypasses the duplicate selection.
