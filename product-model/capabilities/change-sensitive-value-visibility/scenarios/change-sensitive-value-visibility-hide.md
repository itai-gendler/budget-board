---
{
  "kind": "primary",
  "routes": {
    "web": "Web"
  },
  "steps": [
    {
      "text": "The User changes the browser’s sensitive-amount visibility selection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated"
        }
      }
    },
    {
      "text": "The Product restores Browser preferences from browser storage, defaulting to visible if unavailable.",
      "kind": "product",
      "entities": [
        {
          "entity": "browser-preferences",
          "effect": "creates",
          "facts": [
            "Sensitive values hidden"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated"
        }
      }
    },
    {
      "text": "The Product sets the sensitive-amount selection in Browser preferences to true. Sensitive currency formatting then masks amounts and currency-bearing template text. Storage read failure starts visible; storage write failure does not invalidate the current selection.",
      "kind": "product",
      "entities": [
        {
          "entity": "browser-preferences",
          "effect": "changes",
          "facts": [
            "Sensitive values hidden"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "web::authenticated"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "client/src/providers/PrivacyModeProvider/PrivacyModeProvider.tsx"
    }
  ]
}
---

# Change sensitive value visibility hide

## Trigger

The User changes the browser’s sensitive-amount visibility selection.

## Outcome

The Product sets Browser preferences.Sensitive values hidden to true. Sensitive currency formatting then masks amounts and currency-bearing template text. Storage read failure starts visible; storage write failure does not invalidate the current selection.
