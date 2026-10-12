---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/TransactionImportService.cs#TransactionImportService"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Database/Data/UserDataContext.cs#OnModelCreating"
    }
  ]
}
---

# Transaction import

Pending, Running, Completed, Completed with errors, Failed, Cancelled. Expired Running work can return to Pending.

## Information kept

- **Submitted work** — Accepted import row payload retained for asynchronous processing.
- **Status** — Pending, Running, Completed, Completed with errors, Failed or Cancelled work status.
- **Total count** — Accepted row count.
- **Processed count** — Processing count, potentially including replayed work.
- **Succeeded count** — Success count, potentially including skipped existing rows.
- **Failed count** — Failure count.
- **Retry key** — Caller-supplied retry identity returning existing owned work.
- **Cancellation requested** — Whether cancellation has been requested.
- **Error summary** — Retained processing-error summary.
- **Created date** — Work creation time.
- **Started date** — First processing-start time; lease recovery and later claims retain it.
- **Completed date** — Retained completion date.

## States

### Pending

Accepted work awaits a worker.

### Running

A worker has claimed the submitted work.

### Completed

Completion is recorded.

### Completed with errors

Work finished with both successful and failed rows.

### Failed

Processing ended in failure.

### Cancelled

Processing stopped after cancellation.
