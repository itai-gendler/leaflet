---
appliesTo:
- type: capability
  id: sign-in-with-email
- type: capability
  id: change-account-email
- type: entity
  id: user
  facts:
  - Email
references:
- kind: code
  role: implementation
  target: actions/emailAuth.tsx
- kind: code
  role: implementation
  target: src/utils/confirmationEmail.ts
---

# An email code is six characters, works once, and is sent at most once a minute per address

Asking again within a minute reuses the code already sent rather than sending another.
