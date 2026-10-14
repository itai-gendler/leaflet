---
appliesTo:
- type: entity
  id: email-post
  effect: removes
permits:
- related:
  - verb: sends
    entity: publication
  - verb: owns
    entity: user
- related:
  - verb: sends
    entity: publication
  - verb: has
    entity: contributor
  - verb: holds
    entity: user
  when:
  - entity: contributor
    fact: Accepted
    is: true
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

# Unsent email posts are canceled by the publication's owner and contributors

Only an email that has not started sending can be canceled.
