---
scope: The Leaflet web app (writing, publishing, reading, subscriptions, domains and Leaflet Pro) and its payment and email-delivery webhooks.
method: Static inspection of source, schema, specs and in-app copy; nothing was run.
covered:
- description: Leaflet editor, Home, publish and email pages, and sign-in screens
  paths:
  - app/(app)/(editor)/
  - app/(app)/(identity)/(home-pages)/(writer)/
  - app/(app)/(identity)/[leaflet_id]/
  - app/(app)/(identity)/new/
  - app/(app)/(identity)/new-canvas/
  - app/(app)/(identity)/upgrade/
  - app/(app)/(identity)/merge-accounts/
  - app/login/
  - app/template/
- description: Publication creation, dashboard, settings, theme and pages editor
  paths:
  - app/(app)/(identity)/lish/
- description: Published post, publication, profile, tag and Reader pages
  paths:
  - app/(app)/(published)/
  - app/(app)/(identity)/(home-pages)/p/
  - app/(app)/(identity)/(home-pages)/tag/
  - app/(app)/(identity)/(home-pages)/reader/
- description: Server actions for leaflets, publishing, publications, subscriptions, domains, versions and billing
  paths:
  - actions/
- description: Sign-in, unsubscribe, checkout and webhook routes
  paths:
  - app/api/oauth/
  - app/api/auth/
  - app/api/checkout/
  - app/api/webhooks/stripe/route.ts
  - app/api/webhooks/stripe/handle_subscription_updated.ts
  - app/api/webhooks/stripe/handle_subscription_deleted.ts
  - app/api/webhooks/stripe/handle_invoice_payment_failed.ts
  - app/api/webhooks/stripe/handle_checkout_completed.ts
  - app/api/postmark/
  - app/emails/
- description: Scheduled, broadcast and email-post jobs
  paths:
  - app/api/inngest/functions/publish_scheduled_post.ts
  - app/api/inngest/functions/send_email_post.ts
  - app/api/inngest/functions/send_post_broadcast.ts
- description: Document model, editor mutations and block components
  paths:
  - src/replicache/
  - components/Blocks/
  - components/EditorComments/
  - components/ThemeManager/
- description: Publishing, scheduling, email posts, subscriptions, versioning, entitlements and identity logic
  paths:
  - src/utils/publishLeaflet.ts
  - src/utils/publishPublicationPages.ts
  - src/scheduledPosts/
  - src/emailPosts/
  - src/subscriptions/
  - src/versioning/
  - src/entitlements.ts
  - src/auth.ts
  - src/mergeIdentity.ts
  - src/contributorPermissions.ts
  - src/notifications.ts
- description: Subscribe, interaction and settings components
  paths:
  - components/Subscribe/
  - components/Interactions/
  - components/PostSettings.tsx
  - components/AccountEmailForm.tsx
- description: Leaflet Pro product definition
  paths:
  - stripe/products.ts
exclusions:
- description: Icons, layout primitives, styling, fonts and static assets
  paths:
  - components/Icons/
  - components/PageLayouts/
  - components/utils/
  - public/
  - app/globals.css
  - tailwind.config.js
- description: Schema migrations, generated types and database clients
  paths:
  - supabase/
  - drizzle/
  - database.sql
- description: AT Protocol lexicon sources and generated client types
  paths:
  - lexicons/
- description: Firehose indexer and feed service processes
  paths:
  - appview/
  - feeds/
- description: Maintenance and data-migration jobs
  paths:
  - app/api/inngest/functions/fix_incorrect_site_values.ts
  - app/api/inngest/functions/fix_standard_document_postref.ts
  - app/api/inngest/functions/fix_standard_document_publications.ts
  - app/api/inngest/functions/migrate_user_to_standard.ts
  - app/api/inngest/functions/cleanup_deleted_blobs.ts
  - app/api/inngest/functions/cleanup_expired_oauth_sessions.ts
  - tmp_standard-site-migration.md
- description: Tests, test pages, debug pages, scratch work, plans and CI
  paths:
  - app/test/
  - app/debug/
  - scratch/
  - plans/
  - .github/
  - scripts/
  - vitest.config.ts
- description: Agent instructions and skills shipped with the repository
  paths:
  - .claude/
  - .agents/
  - CLAUDE.md
  - skills-lock.json
- description: Marketing, legal and manual pages
  paths:
  - app/about/
  - app/legal/
  - app/manual/
  - app/page.tsx
unmapped:
- description: 'Paid memberships: tiers, Stripe Connect payouts, wallets, members-only posts and paywall (rolled out per account)'
  paths:
  - actions/memberships.ts
  - actions/publications/joinMembership.ts
  - actions/publications/membershipSettings.ts
  - actions/startStripeConnectOnboarding.ts
  - actions/walletPayment.ts
  - components/Memberships/
  - components/StripeConnect/
  - components/Payments/
  - stripe/connect.ts
  - stripe/wallet.ts
  - stripe/schedules.ts
  - app/api/webhooks/stripe/connect/
  - src/membership.ts
  - src/membership.server.ts
  - app/(app)/(identity)/(home-pages)/(writer)/memberships/
  - app/(app)/(published)/lish/[did]/[publication]/membership/
- description: Replies and Questions blocks on posts (rolled out per author)
  paths:
  - actions/replies.ts
  - actions/questions.ts
  - src/documentReplies.ts
  - src/documentQuestions.ts
  - components/Blocks/ReplyBlock/
  - components/Blocks/QuestionsBlock/
- description: AI agent API for reading and editing Leaflets by token
  paths:
  - app/api/ai/
- description: 'Leaflet team admin area: imports from other blogging platforms, subscriber import, entitlement grants and active-user stats'
  paths:
  - app/(app)/(identity)/admin/
  - actions/admin/
  - src/ghostImport/
  - src/substackImport/
  - src/offprintImport/
  - src/import/
  - src/email-subscribers/
  - src/adminAllowlist.ts
  - src/admin/
- description: Publication feeds (RSS, Atom, JSON), sitemaps and standard.site discovery routes
  paths:
  - app/(app)/(published)/lish/[did]/[publication]/rss/
  - app/(app)/(published)/lish/[did]/[publication]/atom/
  - app/(app)/(published)/lish/[did]/[publication]/json/
  - app/(app)/(published)/lish/[did]/[publication]/sitemap.xml/
  - app/(app)/(published)/lish/[did]/[publication]/.well-known/
  - app/(app)/(published)/lish/feeds/
- description: Mention services that let writers mention things from other apps
  paths:
  - mentions/
  - app/api/rpc/[command]/get_user_mention_services.ts
  - app/api/rpc/[command]/proxy_mention_search.ts
- description: Per-publication email notification toggle in the subscription panel and email-to-identity linking
  paths:
  - components/Subscribe/LinkIdentityModal.tsx
- description: Onboarding tutorial and home theme
  paths:
  - app/(app)/(identity)/(home-pages)/(writer)/home/Tutorial/
  - actions/setTutorialState.ts
limitations:
- description: Firehose-driven indexing decides which records made outside Leaflet (subscriptions, comments, recommends) appear
  paths:
  - appview/
  - app/api/inngest/functions/sync_document_metadata.ts
  - app/api/inngest/functions/index_post_mention.ts
- description: Analytics figures come from an external analytics store whose contents could not be inspected
  paths:
  - tinybird.config.mjs
  - app/api/rpc/[command]/get_publication_analytics.ts
---

# Coverage
