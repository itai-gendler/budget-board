---
{
  "entities": [
    {
      "entity": "simplefin-connection",
      "collects": [
        "Access credential"
      ]
    },
    {
      "entity": "lunchflow-connection",
      "collects": [
        "API credential"
      ]
    },
    {
      "entity": "simplefin-organization",
      "shows": [
        "Name",
        "Domain",
        "Provider URL"
      ]
    },
    {
      "entity": "simplefin-account",
      "shows": [
        "Name",
        "Currency",
        "Reported balance",
        "Balance date",
        "Sync start",
        "Last sync",
        "Local account link"
      ],
      "collects": [
        "Sync start",
        "Local account link"
      ]
    },
    {
      "entity": "lunchflow-account",
      "shows": [
        "Name",
        "Institution name",
        "Currency",
        "Reported balance",
        "Balance date",
        "Sync start",
        "Last sync",
        "Local account link"
      ],
      "collects": [
        "Sync start",
        "Local account link"
      ]
    },
    {
      "entity": "account",
      "shows": [
        "Name",
        "Type",
        "Source"
      ],
      "collects": [
        "Name",
        "Type"
      ]
    },
    {
      "entity": "institution",
      "shows": [
        "Name"
      ],
      "collects": [
        "Name"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.Service/SyncService.cs"
    }
  ]
}
---

# External accounts

Provider connections, discovered records and local links. Collects credentials, local Account selection and Sync start. Shows provider metadata and synchronization status. Stored credentials remain concealed.
