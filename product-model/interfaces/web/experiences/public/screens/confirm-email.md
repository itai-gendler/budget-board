---
{
  "entities": [
    {
      "entity": "user",
      "shows": [
        "Email confirmed"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
    }
  ]
}
---

# Confirm email

Confirmation-link process; successful confirmation changes User.Email confirmed. Invalid proof produces a refusal outcome.
