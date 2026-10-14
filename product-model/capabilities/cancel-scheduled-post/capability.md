---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: actions/publications/scheduledPosts.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/save.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/eligibility.ts
---

# Cancel a scheduled post

Return a scheduled, paused or failed post to being an ordinary draft.
