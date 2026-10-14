---
domain: publication-dashboard
references:
- kind: code
  role: implementation
  target: src/emailPosts/types.ts
- kind: code
  role: implementation
  target: src/emailPosts/save.ts
- kind: code
  role: implementation
  target: app/api/inngest/functions/send_email_post.ts
---

# Email post

A publication draft written to go out only by email, never on the web.

## Information kept

- **Title** — the email's subject
- **Description** — its preview text
- **Send mode** — now, at a scheduled time, or to each new subscriber when they subscribe
- **Send at** — when a scheduled email goes out
- **Content** — the draft's content as it was when saved
- **Recipients** — how many subscribers it went to
- **Sent at** — when it went out
- **Problem** — why a paused or failed email did not go out

## States

### Scheduled

Waiting to be sent.

### Active

Sent to each new subscriber as they subscribe.

### Sending

Going out to the subscribers.

### Sent

Delivered to the subscribers it was sent to.

### Failed

Sending went wrong.

### Paused

Not sent because the newsletter is off or the owner no longer holds Leaflet Pro.
