# Stage 8 — Build prompts pack

Generate `./planmysaas-blueprint/08-build-prompts.md`. This is the killer artifact — read all prior stages and write prompts that someone pastes into Cursor / Claude Code / Lovable to actually start building.

## Output structure

```markdown
# Build prompts pack — <Project name>

These prompts are designed for **paste into your AI coding tool** (Cursor, Claude Code, Lovable, Bolt, v0). They reference the architecture, features, and tech stack from the rest of this blueprint.

**Order:** Start with prompt 01 (project bootstrap), then run prompts in numerical order. Each one assumes the previous one ran successfully.

---

## 01 · Project bootstrap

> Use when: starting from an empty folder.

```
You are a senior full-stack engineer. Bootstrap a Next.js 14 project for <Project name>:

- App Router, TypeScript, no Pages Router
- Tailwind CSS + Inter font
- Prisma with Postgres (use Neon for dev — free tier)
- NextAuth.js with Google OAuth + email magic link
- Folder structure:
    src/app/(marketing)/    public pages
    src/app/(app)/          authenticated app
    src/app/api/            API routes
    src/components/         shared UI
    src/lib/                utilities (db, auth, ai)
    prisma/schema.prisma

Generate:
1. package.json with deps locked
2. .env.example with all required keys
3. prisma/schema.prisma with the User, Session, Account models from NextAuth
4. src/lib/db.ts with the Prisma client singleton
5. src/lib/auth.ts with NextAuth config
6. A working /login and /signup page
7. A protected /app/dashboard page that says "Hello {user.email}"

Stop after this — I'll review before adding domain models.
```

---

## 02 · Domain data models

> Use when: bootstrap is reviewed and merged.

```
Add the following Prisma models to schema.prisma. Run prisma migrate dev with the name "<descriptive-name>".

<Insert each entity from architecture stage 4 in Prisma format>

Then generate:
1. src/lib/db/<entity>.ts repositories with typed CRUD helpers for each entity
2. Seed script at prisma/seed.ts that creates 1 admin + 5 demo records of each entity
3. A type-safe /api/<entity>/route.ts for the most-accessed entity

Don't generate UI yet.
```

---

## 03 · Core feature: <F-01 title>

> Use when: data layer is solid.

```
Build the <F-01 title> feature end-to-end. Spec from blueprint:

USER FLOW:
<paste from feature spec>

ACCEPTANCE CRITERIA:
<paste from feature spec>

Generate:
1. src/app/(app)/<route>/page.tsx (RSC, fetches data server-side)
2. src/app/(app)/<route>/_client.tsx for any interactive parts
3. src/app/api/<route>/route.ts API handler
4. Components: <list 3-5 components from frontend stage>
5. Tests for the API handler (Vitest)

Match the design system: brand color <#XXX>, Inter font, 4/8/12/16 spacing scale, 8px border radius.

Stop after this feature works end-to-end. Don't move to F-02 until I confirm.
```

---

## 04 · Core feature: <F-02 title>

> Same template as 03, for the next P0 feature.

(Repeat for top 3-5 P0 features from stage 5.)

---

## 05 · Auth + permissions

> Use after core features exist.

```
Wire role-based access:

- Roles: <list from idea stage>
- For each protected route, add a guard that checks user.role
- Add a withRole(role) HOC for client components
- Add a getServerUser() helper that throws on missing session

Then add:
- /admin layout that redirects non-admins to /app
- /api/* routes return 401 for unauthenticated, 403 for unauthorised
- Audit log for sensitive actions (write to Prisma AuditLog model)
```

---

## 06 · Payments

> Use when revenue flow is needed.

```
Integrate <Razorpay or Stripe> for the <subscription / one-time / usage-based> model.

Plans (from blueprint):
<paste pricing from analysis stage>

Generate:
1. src/lib/billing/<provider>.ts wrapper
2. src/app/api/billing/webhook/route.ts that handles successful payments
3. /pricing page that lists plans
4. /app/billing page where users see their current plan + can upgrade
5. Subscription model in Prisma + migration
6. Email on successful payment (use Resend; template at src/emails/invoice-receipt.tsx)
```

---

## 07 · Frontend polish

> Use when functionality works.

```
Polish the frontend per design system in blueprint:

- Add <Navbar>, <Footer>, <PageHeader> components
- Implement loading skeletons for every async page
- Implement empty states with illustration + CTA
- Implement error boundaries with friendly messages + retry
- Add /404 and /500 pages
- Audit for accessibility: aria-labels on icon buttons, keyboard nav, focus rings
- Lighthouse perf >85 on /, /app/dashboard, /pricing
```

---

## 08 · Marketing site

> Use when you have something to sell.

```
Build the public marketing pages from the blueprint:

ROUTES:
- / (landing — hero, features, pricing teaser, testimonials, FAQ)
- /pricing (full pricing comparison)
- /blog (MDX-based)
- /docs (if API)
- /privacy + /terms

Match the design system. SEO basics: per-page metadata.title + .description + .openGraph + canonical. JSON-LD for Organization + Product on / and /pricing. Sitemap at /sitemap.xml.
```

---

## 09 · Production deploy

> Use when ready to go live.

```
Set up production deploy:

1. Vercel project linked to main branch
2. Neon production database with connection pooling
3. Cron job for daily cleanup (cancel stale sessions, etc.)
4. Sentry for error tracking
5. PostHog for product analytics
6. Status page (BetterStack or Instatus)
7. Domain + SSL
8. Email warmup with Resend (verify SPF, DKIM, DMARC)

Provide a CHECKLIST.md I can run through before going live.
```

---

## How to use

1. Open Cursor / Claude Code / Lovable
2. Start with prompt 01, paste it as-is
3. Review the output, commit it
4. Move to prompt 02. Don't skip ahead.
5. After prompt 04, you have a working MVP. Show it to 5 friends.
6. Use prompts 05-09 as you need them, not all at once.

## Tips

- **Don't paste all 9 prompts at once.** AI tools work best one prompt at a time.
- **Commit after each prompt** — easy rollback if something goes wrong.
- **Customise the data models** — these are starting points, your domain knowledge wins.
- **Replace vendor names** if you prefer different stacks (Stripe vs Razorpay, Supabase vs Neon).
```

## Quality rules

- Each prompt must be **self-contained** — paste it cold into a new Cursor session and it should work.
- Reference specifics from prior stages (entity names, feature IDs, route paths) — don't be generic.
- 8-10 prompts total. Less = under-spec'd. More = overwhelming.
- Each prompt has a clear **stopping point** ("don't move to next feature until I confirm") so the user stays in control.

## Tone

Hand-off doc to a senior engineer using AI tooling. Tight, opinionated, no fluff.
