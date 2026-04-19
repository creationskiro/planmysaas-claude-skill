# Stage 4 — System architecture

Generate `./planmysaas-blueprint/04-architecture.md`. Read prior stages.

## Output structure

```markdown
# System architecture — <Project name>

## Containers (top-level)
3-5 deployable units. For each: name · purpose · tech choice · external integrations.

Typical containers:
- Web app / mobile app
- API gateway / backend
- Worker / background jobs
- Admin portal
- Marketing site

## Services (10-25 microservices or modules)

Group by domain. For each service:
- **Name** (e.g. `Identity & Access Service`)
- **Type** — `service` / `module` / `store` / `external`
- **Purpose** (one sentence)
- **Owns data**: which entities (e.g. User, Session)
- **Talks to**: 2-3 other services it calls

End with a "node count by type" summary (Modules: X, Services: Y, Stores: Z).

## Data models (8-15 core entities)

For each: entity name · 5-10 key fields with types · relations (e.g. `User has many Course`).

Format as compact ER-style:
```
User
  id            string  PK
  email         string  UNIQUE
  name          string
  role          enum(student, instructor, admin)
  createdAt     timestamp
  → has many Enrollment
  → has many QuizAttempt
```

## API surface (top 20 endpoints)

Group by service. Format: `METHOD /path` · purpose · auth required (yes/no).

Example:
```
POST   /api/auth/signup        Create account                  no
GET    /api/courses             List courses                    no
POST   /api/courses/:id/enroll  Enroll in course                yes
```

## Background jobs (5-10)

Async workers. For each: trigger · what it does · failure mode.

## External integrations

For each: vendor · purpose · pricing tier · failover plan.

Common: payment (Razorpay/Stripe), email (Resend), auth (Google OAuth), storage (S3), AI (Claude/OpenAI).

## Tech stack (one row per layer)

| Layer        | Choice                  | Why |
|--------------|-------------------------|-----|
| Frontend     | Next.js 14 (App Router) | RSC + streaming |
| Database     | Postgres + Prisma       | ACID + types |
| Background   | BullMQ + Redis          | Reliable retries |
| Hosting      | Vercel + Neon           | Zero ops |
| AI           | Claude Sonnet 4.6       | Long context |
| Payments     | Razorpay                | India-first |

## Connections diagram (textual)

ASCII or list-form: which container calls which service, sync vs async. Replace with a generated mermaid diagram if user prefers.
```

## Quality rules

- Service names should be **named after the domain**, not the tech (e.g. `Course Management Service`, not `Postgres Service`).
- Every service must own data XOR be a pure orchestrator. No "god services".
- Tech stack must be **opinionated** — pick one option per layer, justify in 4-6 words.
- API endpoints must follow REST conventions; no `/getUser` style.
- If the project is mobile-first, lead with mobile container; web is secondary.

## Tone

Senior architect briefing the engineering team. Confident defaults, escape hatches noted.
