---
{
  "id": "budget-board",
  "summary": "Track financial records, monthly category Budgets and account-linked Goals, with imports, automation, provider Sync and configurable financial reporting.",
  "category": "personal-finance",
  "tags": [
    "budgeting",
    "financial-goals",
    "personal-finance"
  ],
  "authors": [
    {
      "name": "teelur",
      "url": "https://github.com/teelur"
    }
  ],
  "license": "AGPL-3.0-only",
  "languages": [
    "en-US",
    "de",
    "fr",
    "pt-BR",
    "zh-Hans",
    "id",
    "it",
    "ru"
  ],
  "limitations": [
    "Goal contributions and Budget availability do not reserve funds or execute payments.",
    "Provider monetary values are used without currency conversion.",
    "Forecast occurrences are projections rather than ledger Transactions."
  ],
  "references": [
    {
      "kind": "doc",
      "role": "context",
      "target": "README.md"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/App.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Program.cs"
    }
  ]
}
---

# Budget Board

A personal finance workspace for recording Accounts, Assets and Transactions, planning monthly category Budgets and account-linked Goals, importing records, applying classification and recurring rules, synchronizing financial providers and interpreting financial results through Trends and configurable dashboard widgets.
