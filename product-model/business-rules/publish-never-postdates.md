---
appliesTo:
- type: capability
  id: publish-post
- type: entity
  id: post
  facts:
  - Published at
references:
- kind: code
  role: implementation
  target: actions/publishToPublication.ts
---

# Publishing never dates a post in the future

A post may be backdated; a future date on Publish publishes it now, and a post for later is scheduled instead.
