---
appliesTo:
- type: entity
  id: publication-page
  effect: creates
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

# Only a publication's owner adds its pages

Customizing a publication's pages and navigation is the owner's.
