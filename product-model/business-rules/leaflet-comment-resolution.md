---
appliesTo:
- type: entity
  id: leaflet-comment
  effect: removes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Bluesky account
    present: true
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
---

# Signed-in writers with a Bluesky account resolve comment threads on Leaflets

Resolving removes the thread with its replies for everyone.
