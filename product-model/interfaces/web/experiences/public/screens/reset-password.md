---
{
  "entities": [
    {
      "entity": "local-login",
      "collects": [
        "Password credential"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Unauthorized/ResetPassword/ResetPassword.tsx"
    }
  ]
}
---

# Reset password

The replacement-password stage collects the new credential and reset-code proof for the email supplied at Login. A successful reset returns the same User to Login.
