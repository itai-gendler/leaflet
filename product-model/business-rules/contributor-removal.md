---
appliesTo:
- type: entity
  id: contributor
  effect: removes
permits:
- related:
  - verb: has
    entity: publication
  - verb: owns
    entity: user
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

# A publication's owner removes contributors, and contributors remove themselves

The owner removes any contributor or pending invitation; a contributor may leave.
