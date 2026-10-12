---
{
  "actors": [
    "user"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Unauthorized/Welcome.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
    }
  ]
}
---

# Confirm email after Login refusal

## Goal

Confirm the existing address after a Login refusal.

## Success criterion

The resent confirmation link confirms the same email.
