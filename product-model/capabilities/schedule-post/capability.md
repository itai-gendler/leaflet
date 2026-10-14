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
- kind: code
  role: implementation
  target: app/api/inngest/functions/publish_scheduled_post.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/publish.ts
---

# Schedule a post

Set a publication draft to publish at a later time with the sharing chosen now; the post publishes itself when the time comes. Scheduling is a Leaflet Pro feature of the publication's owner.
