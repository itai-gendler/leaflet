---
appliesTo:
- type: entity
  id: email-post
  effect: changes
permits:
- unattended: true
references:
- kind: code
  role: implementation
  target: src/emailPosts/save.ts
- kind: code
  role: implementation
  target: src/emailPosts/eligibility.ts
- kind: code
  role: implementation
  target: app/api/inngest/functions/send_email_post.ts
---

# Only the Product moves an email post through sending

Writers queue an email post; sending, delivery and pausing happen on the Product's own schedule.
