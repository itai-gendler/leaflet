---
appliesTo:
- type: entity
  id: publication
  effect: changes
  facts:
  - Newsletter
permits:
- related:
  - verb: owns
    entity: user
  when:
  - entity: user
    fact: Leaflet Pro
    is: true
references:
- kind: code
  role: implementation
  target: actions/publications/newsletterSettings.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/SettingsContent.tsx
---

# Only a publication's owner with Leaflet Pro turns its newsletter on or off

Newsletter mode is a Leaflet Pro feature of the owner; the Newsletter settings show the upgrade offer to owners without it.
