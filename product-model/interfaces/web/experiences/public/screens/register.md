---
{
  "entities": [
    {
      "entity": "user",
      "collects": [
        "Email"
      ]
    },
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
      "target": "client/src/app/Unauthorized/Register/Register.tsx"
    }
  ]
}
---

# Register

Registration process. Collects User.Email, Local login.Password credential.
