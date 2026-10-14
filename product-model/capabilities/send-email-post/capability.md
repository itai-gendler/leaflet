---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: actions/publications/emailPosts.ts
- kind: code
  role: implementation
  target: src/emailPosts/save.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/email/SendEmail.tsx
- kind: code
  role: implementation
  target: app/api/inngest/functions/send_email_post.ts
- kind: code
  role: implementation
  target: src/emailPosts/onSubscribe.ts
---

# Send an email post

Send an email-only draft to the publication's email subscribers now, at a scheduled time, or to each new subscriber when they subscribe. Email posts need the newsletter on and a Leaflet Pro owner.
