---
appliesTo:
- type: entity
  id: leaflet-comment
  effect: changes
  facts:
  - Replies
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

# Signed-in writers with a Bluesky account reply to and delete replies in comment threads on Leaflets

Replies carry their author's Bluesky identity.
