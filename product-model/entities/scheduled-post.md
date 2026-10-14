---
domain: publication-dashboard
references:
- kind: code
  role: implementation
  target: src/scheduledPosts/types.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/save.ts
- kind: code
  role: implementation
  target: app/api/inngest/functions/publish_scheduled_post.ts
---

# Scheduled post

A publication draft set to publish at a chosen time, with the sharing choices it will publish with.

## Information kept

- **Publish at** — when it will publish
- **Sharing** — whether it will be emailed, shown in Discover and shared on Bluesky with the post text composed when scheduling
- **Scheduled by** — who scheduled it; the post publishes as them
- **Problem** — why a paused or failed post did not publish

## States

### Scheduled

Waiting for its time.

### Paused

Not published because the publication's owner no longer holds Leaflet Pro.

### Failed

Not published because publishing went wrong, such as the owner being signed out of Bluesky.
