---
references:
- kind: code
  role: implementation
  target: actions/pollActions.ts
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/voteOnPublishedPoll.ts
---

# Poll vote

One voter's choice in a poll, in a Leaflet or on a published post.

## Information kept

- **Options** — the options chosen
- **Voter** — who voted: the signed-in account, or this browser when nobody is signed in; on a published post, the voter's Bluesky account
