---
domain: reader
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Comments/commentAction.ts
- kind: code
  role: implementation
  target: src/comments/tombstoneComment.ts
---

# Comment on a post

A reader's comment on a published post, or a reply to another comment, kept as a record in their Bluesky account.

## Information kept

- **Text** — what the comment says, with mentions
- **Quoted passage** — the passage of the post it quotes, if any
- **In reply to** — the comment it replies to, if any
- **Posted at** — when it was posted
