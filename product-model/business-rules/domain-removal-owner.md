---
appliesTo:
- type: entity
  id: domain
  effect: removes
permits:
- related:
  - verb: owns
    entity: user
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
---

# Only a domain's owner deletes it

Deleting removes the domain from Leaflet and from the account.
