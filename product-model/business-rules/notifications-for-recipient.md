---
appliesTo:
- type: entity
  id: notification
  effect: reads
permits:
- related:
  - verb: receives
    entity: user
references:
- kind: code
  role: implementation
  target: actions/getNotifications.ts
---

# Only the recipient sees their notifications

Each person's notifications are theirs alone.
