---
references:
- kind: code
  role: implementation
  target: src/notifications.ts
- kind: code
  role: implementation
  target: actions/getNotifications.ts
---

# Notification

Something that happened to a person's posts, publications or comments: a comment or reply, a mention, a recommend, a new subscriber, a quote or embed on Bluesky.

## Information kept

- **Kind** — what happened
- **Subject** — the post, comment, publication or Bluesky post it is about
- **Created at** — when it happened

## States

### Unread

Not yet seen.

### Read

Seen on the notifications page.
