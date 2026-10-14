---
appliesTo:
- type: capability
  id: merge-accounts
- type: entity
  id: user
  facts:
  - Bluesky account
references:
- kind: code
  role: implementation
  target: actions/mergeIdentity.ts
- kind: code
  role: implementation
  target: src/mergeIdentity.ts
---

# Only an email-only account merges, and only into an account with a Bluesky account

An account already connected to Bluesky is never merged away.
