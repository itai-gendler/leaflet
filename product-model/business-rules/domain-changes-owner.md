---
appliesTo:
- type: entity
  id: domain
  effect: changes
permits:
- related:
  - verb: owns
    entity: user
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
---

# Only a domain's owner points it somewhere or clears it

Assigning a domain to a Leaflet or publication, unassigning it and checking its status are its owner's; a domain is pointed at a publication only by someone who owns both.
