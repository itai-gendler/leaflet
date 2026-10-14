---
appliesTo:
- type: entity
  id: email-post
  effect: creates
permits:
- related:
  - verb: sends
    entity: publication
  - verb: owns
    entity: user
  when:
  - entity: publication
    fact: Newsletter
    is: true
  - entity: publication
    fact: Pro features
    is: true
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
  - entity: publication
    fact: Newsletter
    is: true
  - entity: publication
    fact: Pro features
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

# Email posts are sent by a publication's owner and contributors while its newsletter is on and its owner holds Leaflet Pro

Email-only posts are a Leaflet Pro feature of the owner and need newsletter mode for anyone to send to.
