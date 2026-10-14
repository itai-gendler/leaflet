---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: actions/pollActions.ts
---

# Vote in a poll

Vote in a Leaflet's poll, with or without an account; voting again changes the vote.
