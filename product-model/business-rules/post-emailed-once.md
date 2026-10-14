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
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: app/api/inngest/functions/send_post_broadcast.ts
- kind: code
  role: implementation
  target: app/api/inngest/functions/sync_document_metadata.ts
---

# A post is emailed to subscribers once, when it is first published with the newsletter on

Updating or republishing a post never emails it again, posts published before the newsletter was turned on are never emailed, and a post published quietly or with email turned off is never emailed later.
