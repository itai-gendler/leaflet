---
appliesTo:
- type: entity
  id: contributor
  effect: changes
  facts:
  - Accepted
permits:
- related:
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: actions/publications/contributors.ts
- kind: code
  role: implementation
  target: src/contributorPermissions.ts
---

# Only the invited person accepts a contributor invitation

An invitation is accepted by the Bluesky account it was sent to.
