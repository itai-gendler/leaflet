---
appliesTo:
- type: entity
  id: publication
  effect: creates
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
  target: app/(app)/(identity)/lish/createPub/createPublication.ts
---

# Creating a publication needs a Bluesky account

A publication is a record in its owner's Bluesky account, so an account signed in by email only connects Bluesky first.
