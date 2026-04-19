# Stage 7 — Phases + release plan

Generate `./planmysaas-blueprint/07-phases.md`. Read prior stages.

## Output structure

```markdown
# Phases + release plan — <Project name>

## Total scope summary
- Total features: <from stage 5>
- Total services: <from stage 4>
- Estimated MVP timeline: <X weeks>
- Estimated v1.0 timeline: <Y weeks>
- Estimated team: <Z people>

## Phase 0 — Foundation (Week 0-1)

Goal: codebase ready, deploy pipeline working, no users yet.

**Tasks:**
- Repo setup (monorepo / single, Next.js + Prisma)
- Auth scaffolding (signup, login, sessions)
- Database schema migration
- Deploy to staging (Vercel + Neon)
- Error monitoring (Sentry)
- Analytics (PostHog or similar)

**Exit criteria:** A test user can sign up, log in, see an empty dashboard.

## Phase 1 — MVP (Week 2-5)

Goal: ship the smallest thing that delivers the core promise. Ship to 10 friendly users.

**Features (from stage 5):**
- F-01, F-02, F-04, F-07, F-12 (whichever P0s map to the wedge)

**Tasks broken down:**
- Week 2: backend services for those features
- Week 3: frontend pages + flows
- Week 4: payment integration if revenue model needs it
- Week 5: polish, bugs, internal testing

**Exit criteria:**
- 5 friendly users complete the core flow end-to-end
- 0 P0 bugs
- Lighthouse perf >85 on landing + key flows

## Phase 2 — Public launch (Week 6-9)

Goal: Product Hunt / Twitter / community launch. First 100 paying users.

**Features added:**
- Onboarding improvements (F-XX)
- Email lifecycle (welcome, day-3 nudge, win-back)
- Referrals or social proof
- Admin dashboard basics

**Marketing:**
- Landing page polish (above-fold, social proof, FAQ)
- 1 long-form blog ("How we built X with Y")
- Demo video (60s)
- Launch on PH + HN + relevant subreddits

**Exit criteria:**
- 100 signups
- 10 paying users
- NPS or D7 retention measured

## Phase 3 — Growth (Week 10-16)

Goal: 1k users, $5k MRR.

**Features added:**
- Power-user features (bulk actions, exports, integrations)
- Team / collaboration if applicable
- Advanced analytics for users

**Growth tactics:**
- SEO (5-10 long-tail content pages)
- Free tools / calculators that link to product
- Partner with 1-2 communities

## Phase 4 — Scale (Month 5+)

Goal: $20k+ MRR, hire first engineer.

**Features:**
- API for power users
- Admin v2 (audit logs, role granularity)
- Performance optimization (DB indexes, caching, CDN)

## Risk register (from stage 3)

Re-list top 5 risks with phase-aware mitigation.

| Risk                            | Phase impacted | Mitigation                                   |
|---------------------------------|----------------|----------------------------------------------|
| Free substitutes (YouTube/GPT)  | Phase 2-3      | Ship outcomes-based positioning by Week 6    |
| ...                             |                |                                              |

## Decision log (initial 5 decisions)

Record initial trade-offs so future-you remembers why.

1. **Chose Next.js over Remix** — RSC + Vercel deploy ease.
2. **Chose Postgres over Mongo** — ACID + structured course data.
3. **Skipped mobile native for MVP** — PWA covers 90% of need until Phase 3.
4. **Razorpay over Stripe** — India-first audience.
5. **Single-region deploy** — defer multi-region until 5k users.

## Initiatives (cross-cutting)

3-5 longer-running streams that don't fit a single sprint:
- **Onboarding excellence** (continuous A/B)
- **Performance budget** (continuous)
- **Documentation** (continuous)
- **Community** (Discord / Slack from Phase 2)
```

## Quality rules

- Estimates must be **honest** — most solo founders overestimate by 2-3x. Use historical solo-founder benchmarks: MVP = 4-6 weeks, not 2.
- Each phase has a **single goal sentence**, not a list of goals.
- Exit criteria must be **observable** — "users sign up" not "great UX".
- Risks reference stage 3 to stay grounded.

## Tone

Pragmatic engineering manager. No happy-path-only thinking — call out risks at each phase.
