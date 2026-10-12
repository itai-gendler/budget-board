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
    },
    {
      "entity": "recovery-code",
      "collects": [
        "Credential"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/app/Unauthorized/Login/Login.tsx"
    }
  ]
}
---

# Login

Authentication process, including authenticator and recovery-code stages. Collects User.Email, Local login.Password credential, Recovery code.Credential. Proof codes and remember-me choice are temporary inputs.
