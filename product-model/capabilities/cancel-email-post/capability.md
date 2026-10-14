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
---

# Cancel an email post

Stop an unsent email post, returning it to an ordinary email-only draft.
