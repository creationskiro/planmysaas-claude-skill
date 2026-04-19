# Cursor / Claude Code prompt pack — quick reference

Paste these into Cursor or Claude Code in the order shown. Each builds on the last.

## Setup

```
You're working on a Next.js 14 + TypeScript + Prisma + Postgres project. Read the blueprint files in ./planmysaas-blueprint/ before answering anything. Use the architecture in 04-architecture.md and design system in 06-frontend.md as your defaults.
```

Run this once at session start so the AI has the full context.

## Common patterns

### Add a new feature
```
Add feature F-XX from 05-features.md. Build:
- Server component page
- API route
- Repository in src/lib/db/
- Tests
Match the design system in 06-frontend.md.
```

### Refactor a service
```
Look at the <Service name> definition in 04-architecture.md. The current code in src/lib/services/<name>.ts has drifted — refactor to match the spec, add JSDoc, add 3 unit tests.
```

### Add an admin view
```
Add an admin page at /admin/<entity>. List view with filters from 06-frontend.md design tokens. Include: pagination, search, role-based action buttons. Wrap mutations in withAudit() helper.
```

### Wire payments
```
Integrate Razorpay using the plan structure from 03-analysis.md. Generate the webhook handler, plan creation script, and the /pricing → checkout flow. Use Prisma Subscription model.
```
