---
id: leaflet
summary: 'Shared writing and social publishing: instant collaborative docs, and publications people follow, built on Bluesky.'
category: publishing
tags:
- writing
- collaborative-documents
- blogging
- newsletters
- bluesky
- atproto
authors:
- name: Learning Futures Inc. (Leaflet)
  url: https://leaflet.pub
license: MIT
languages:
- en
limitations:
- People sign in with their Bluesky account or with a code sent to their email; Leaflet keeps no passwords.
- Publications, posts, comments, recommends and Bluesky subscriptions live in the writer's or reader's own Bluesky account; publishing, commenting and subscribing with Bluesky need a connected Bluesky account.
- Anyone holding a Leaflet's edit link can edit it, with or without an account.
- Newsletter emails are sent from Leaflet's own sending address; replies go to the publication's verified reply-to address.
- Leaflet Pro is a single paid plan, billed monthly or yearly through Stripe's hosted checkout and billing portal.
references:
- kind: code
  role: implementation
  target: README.md
- kind: code
  role: implementation
  target: CLAUDE.md
- kind: code
  role: implementation
  target: src/entitlements.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/upgrade/page.tsx
- kind: spec
  role: intent
  target: specs/2026-02-03-pro-tier.md
- kind: spec
  role: intent
  target: specs/2026-04-20-newsletter-mode.md
---

# Leaflet

Leaflet is a web app for shared writing and social publishing. Anyone can make a Leaflet — an instant collaborative document of blocks (text, images, embeds, polls, sub-pages and canvases) — without an account, and share it by its edit link or a read-only view link. People who sign in keep their Leaflets on Home, comment on them, keep a version history and publish them: as a standalone Looseleaf on their profile, or as a post of a Publication. A Publication is a blog or newsletter with its own address, theme, pages and subscribers; its owner manages it from a dashboard, invites contributors, sends posts by email, schedules posts, reads its analytics and points custom domains at it. Readers read posts, subscribe with Bluesky or by email, recommend and comment, and follow what they subscribe to in the Reader. Publications, posts, comments, recommends and subscriptions are records in the person's own Bluesky (AT Protocol) account. Leaflet Pro, a paid plan, unlocks analytics, email newsletters, post scheduling, group publications and version history.

## Intent

Leaflet is "a tool for shared writing and social publishing": make Leaflets, instant collaborative docs with rich media, multiple pages and more, with no account needed; and create Publications, like blogs or newsletters, that friends can follow — built on Bluesky. Leaflets serve shared notes and docs, collections, wikis and homepages; Publications serve blogs, newsletters and project logs — anything people want others to read and follow.
