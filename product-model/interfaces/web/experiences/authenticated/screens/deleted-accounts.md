---
{
  "entities": [
    {
      "entity": "account",
      "shows": [
        "Name",
        "Source",
        "Deletion date"
      ]
    },
    {
      "entity": "institution",
      "shows": [
        "Name"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Controllers/AccountController.cs"
    }
  ]
}
---

# Deleted accounts

Recovery and permanent-removal context. Shows Account.Name/Source/Deletion date and Institution.Name.
