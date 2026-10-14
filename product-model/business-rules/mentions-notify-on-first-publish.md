---
appliesTo:
- type: capability
  id: publish-post
- type: capability
  id: comment-on-post
- type: entity
  id: notification
references:
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: src/notifications.ts
---

# People, publications and posts mentioned in a post are notified when it is first published

Comments notify the post's author or the replied-to commenter and anyone they mention; recommends, new Bluesky subscribers and Bluesky posts quoting or embedding a post notify its author.
