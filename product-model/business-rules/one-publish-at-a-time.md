---
appliesTo:
- type: capability
  id: publish-post
- type: capability
  id: update-post
- type: entity
  id: post
references:
- kind: code
  role: implementation
  target: src/utils/publishLock.ts
---

# A draft publishes one run at a time

A second publish of the same draft while one is running is refused, so a double submit never makes two posts.
