---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "server/BudgetBoard.WebAPI/Program.cs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/shared/projectEnvVariables.ts"
    }
  ],
  "singleton": true
}
---

# Deployment settings

The Product’s deployment settings, including independent browser/server feature switches and synchronization scheduling.

## Information kept

- **Server local auth disabled** — Server switch closing public local authentication.
- **Server new users disabled** — Server switch closing registration and new external provisioning.
- **Server OIDC enabled** — Server switch enabling the external login method.
- **Email confirmation required** — Whether local authentication requires confirmed email.
- **Demo mode** — Server switch activating scoped demo restrictions.
- **Automatic sync disabled** — Whether the scheduled synchronization job is disabled.
- **Sync interval hours** — Configured interval; default eight hours, minimum one hour.
- **Browser local auth disabled** — Browser switch controlling offered local-authentication controls.
- **Browser new users disabled** — Browser switch controlling offered registration controls.
- **Browser OIDC enabled** — Browser switch controlling offered external-login controls.
- **Browser demo mode** — Browser demo setting, independently supplied from server settings.
