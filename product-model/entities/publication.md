---
domain: publication-settings
relations:
- entity: post
  verb: has
  cardinality: one-to-many
- entity: contributor
  verb: has
  cardinality: one-to-many
- entity: leaflet
  verb: holds draft
  cardinality: one-to-many
- entity: publication-page
  verb: has
  cardinality: one-to-many
- entity: subscription
  verb: gains
  cardinality: one-to-many
- entity: email-subscription
  verb: gains
  cardinality: one-to-many
- entity: email-post
  verb: sends
  cardinality: one-to-many
- entity: scheduled-post
  verb: schedules
  cardinality: one-to-many
- entity: domain
  verb: answers at
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/createPub/createPublication.ts
- kind: code
  role: implementation
  target: actions/publications/updatePublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/SettingsContent.tsx
---

# Publication

A blog or newsletter: a named collection of posts at its own address, with a theme, pages, subscribers and settings. It lives in its owner's Bluesky account.

## Information kept

- **Name** — the publication's name
- **Description** — its description
- **Logo** — its icon
- **Address** — its leaflet.pub subdomain, chosen at creation
- **Theme** — its colors, background, fonts and page width
- **Layout** — whether posts show previous/next and first/last buttons, and in which direction
- **Sharing preferences** — whether it shows in Discover and its posts show comments, mentions, recommends and other publications on tag pages
- **Recommended publications** — other publications it recommends to its readers, in order
- **Pages** — its published home page and navigation pages
- **Newsletter** — whether newsletter mode is on, letting readers subscribe by email and posts go out by email
- **Reply-to email** — the address readers' replies to its emails go to
- **Reply-to verified** — whether the reply-to address has been confirmed
- **Pro features** — whether its owner holds Leaflet Pro, which its contributors use too
- **Analytics** — visits to its pages and posts over time, top referrers and pages, subscriber growth and the Bluesky posts that link to it
