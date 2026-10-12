---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User selects export columns and their order for the current filters and requests CSV.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::export-transactions"
        }
      }
    },
    {
      "text": "The Product downloads the selected filtered Transaction facts and Account.Name as transactions.csv, in the selected column order. Shipped fields are Date, Merchant, Amount, classification preferring Subcategory, Account name, Notes, Pending and Source. Fields are quote-escaped; Pending is the default false response input rather than a retained fact. Export does not include label.",
      "kind": "product",
      "entities": [
        {
          "entity": "transaction",
          "effect": "reads",
          "facts": [
            "Date",
            "Merchant",
            "Amount",
            "Category",
            "Subcategory",
            "Notes",
            "Source"
          ]
        },
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Name"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated::export-transactions"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Authorized/PageContent/Transactions/TransactionsHeader/ExportTransactionsModal/ExportTransactionsModal.tsx"
    }
  ]
}
---

# Export transactions filtered csv

## Trigger

The User selects export columns and their order for the current filters and requests CSV.

## Outcome

The Product downloads the selected filtered Transaction facts and Account.Name as transactions.csv, in the selected column order. Shipped fields are Date, Merchant, Amount, Category preferring Subcategory, Account name, Notes, Pending and Source. Fields are quote-escaped; Pending is the default false response value rather than a retained fact. Export does not include Tags.
