---
appliesTo:
- type: entity
  id: publication-page
  effect: removes
permits:
- related:
  - verb: has
    entity: publication
  - verb: owns
    entity: user
references:
- kind: code
  role: implementation
  target: src/utils/publishPublicationPages.ts
---

# Only a publication's owner removes its pages

Removing a page or link from the publication's navigation is the owner's.
