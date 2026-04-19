# Stage 8 — Build playbook (the most important artifact)

Generate `./planmysaas-blueprint/08-build-playbook.md`. This is **not** a list of paste-ready prompts. It is a deep, decision-grade build instruction set — the kind a staff engineer would write for a junior team. The user (or their AI coding tool, or a future contractor) will follow this step-by-step to ship the product.

Read every prior stage (01–07) before generating. Cross-reference the actual entity names, feature IDs, route paths, tech stack, and wedge from earlier files. A generic playbook is a failed playbook.

## Required output structure

The playbook follows a strict **dependency-tree build order — leaf to root**. Foundation primitives first, then data, services, features, polish, ship. Each step is a node in the tree; later steps cannot start until earlier steps' rubrics pass.

Use this exact skeleton for the output file. Do not deviate — consistency is what makes the playbook usable.

```markdown
# Build playbook — <Project name>

> Decision-grade build instructions for the <Project name> SaaS.
> Follow steps in order. Do not skip rubric items. Stop and review at the gate after every step.

## How to use this playbook

[2 short paragraphs:]
- This is a build sequence, not a wishlist. Each step depends on the previous one.
- After every step there is a "stop and review" gate. Do not advance until every rubric item checks. The next step assumes everything before it works.

## Build sequence — at a glance

[A textual dependency tree — leaf at top, root at bottom. Every step listed with its dependency arrow. Example:]

```
01 Repo bootstrap + deploy pipeline       (no deps — leaf)
   └─ 02 Data layer (Prisma schema)
        └─ 03 Service layer + repositories
             └─ 04 Auth + permissions
                  └─ 05 Core feature P0-1 (<F-XX from stage 05>)
                       └─ 06 Core feature P0-2 (<F-XX>)
                            └─ 07 Core feature P0-3 (<F-XX>)
                                 └─ 08 Payments + billing
                                      └─ 09 Frontend polish (loading/empty/error states)
                                           └─ 10 Marketing site + SEO
                                                └─ 11 Production deploy + observability
                                                     └─ 12 Post-launch ops & runbooks (root)
```

(Adjust 9–12 steps based on the project's wedge. If the business model is free, skip step 08. If mobile-first, add a mobile-bridge step.)

---

## Build Step 01 — Repo bootstrap & deploy pipeline

### 🎯 Goal
[One sharp sentence — what "done" looks like for this step. Must be observable.]

### 📍 Why this is the leaf
[1 paragraph — what every later step assumes. Why nothing else works without this.]

### 📥 Inputs (preconditions before you start)
[Bulleted list — tools to install, accounts to have, env values to acquire. If empty, write "None — this is the leaf step."]

### 📤 Outputs (what exists after this step passes)
[Bulleted list — observable artifacts. Files, deployed URLs, working flows. The user must be able to point at each one and say "yes, that exists now."]

### 🛠 Implementation details

**Files to create:**
[Tree-style list with one-line purpose per file]

**Tech decisions** (locked from blueprint stage 04 — do not re-litigate):
[Bulleted: tech choice — reason. 4–6 items.]

**Patterns (mandatory across the codebase):**
[3–6 bullets. Code conventions every later step assumes. e.g. "All async DB calls return typed Result<T>", "Auth helpers live in src/lib/auth/, never inline in routes".]

### ✅ Acceptance rubric
[8–14 testable checkboxes. Every item must be observable — "user can do X", "command Y returns Z", "page A renders B". No vague "code is clean" items. The reviewer (human or AI) checks each box; if any box fails, the step is not done.]

### ⚠️ Edge cases to handle
[3–5 bullets. Race conditions, expired tokens, empty states, failure modes specific to this step. Each one names the scenario + the required behavior.]

### ❌ Common pitfalls (do NOT do these)
[4–7 bullets. Specific anti-patterns drawn from real failed shipments. Each one starts with "Don't" or "Never". Add a half-line on why it's a trap.]

### 📊 Quality bar
[3–5 measurable thresholds. Lighthouse score, npm audit, test coverage, p95 latency, bundle size — whatever's relevant to this step.]

### 🛑 Stop and review (gate before next step)
[A 3–5 step verification sequence the user runs before moving on. Concrete actions: "Sign up, log out, log in three times. No errors." If any verification fails, the step is not done — do not advance.]

---

## Build Step 02 — Data layer

[Same skeleton — every section filled with project-specific detail referencing entities from blueprint stage 04.]

---

[... continue for every step in the dependency tree ...]

---

## Final ship checklist

[A 10–14 item launch checklist that aggregates outputs from every prior step. Each item observable.]

## What to do when a step fails

[3–5 short rules. e.g.:]
1. **Don't skip ahead.** Each step is a foundation. Skipping creates a debt you'll pay 10x later.
2. **Re-read the dependency.** Most failures are caused by a missed input from the prior step.
3. **Check the pitfalls list first** — it exists because someone shipped a bug there before.
4. **Bisect the failing rubric item.** Identify the smallest change that broke it; revert if needed.
5. **If still stuck**, paste the failing rubric item into Claude Code with the playbook open. Reference this file by name so Claude has the full context.

## Why this playbook is different from generic build prompts

[3 short paragraphs about how this playbook is project-specific (references entities, features, wedge from earlier stages), how it sequences (leaf to root, no skipping), and how it gates (rubric must pass before next step). End with: "If a step feels generic, you're missing context — re-read the relevant blueprint stage first."]
```

## Operating rules for generating the playbook

1. **Step count: 9–12.** Less means under-spec'd; more means death by a thousand cuts.

2. **Always reference blueprint stages by name and ID.** "Build feature F-01 from stage 05" — never just "build the first feature". The cross-references are what make the playbook decision-grade.

3. **Acceptance rubrics must be observable.** Every checkbox is something a human can verify in under 60 seconds. No "code is clean", no "performance is good". Yes "Lighthouse perf ≥ 90 on /pricing" or "User can sign up → confirm email → log in within 2 minutes end-to-end".

4. **Pitfalls must be specific.** Generic ("don't write bad code") is rejected. Specific ("don't put NEXTAUTH_SECRET in committed code — it must be env-only") is required. Pitfalls come from real-world failure modes for the chosen stack.

5. **Quality bars must be measurable.** Numbers, not adjectives. "Zero P0 bugs in 24h of test traffic" not "stable". "Bundle size < 250KB gzipped" not "small".

6. **Stop-and-review gates must be active verifications.** Concrete steps the user runs (commands, clicks, observations) — not "make sure it works".

7. **Tech choices are locked.** The tech stack from stage 04 is the source of truth. Do not propose alternatives in this playbook. If the user wants to change the stack, they go back to stage 04 and re-run that.

8. **Tone: senior engineer briefing a team.** Direct, specific, no marketing language, no emoji-heavy enthusiasm. The emoji headers (🎯 📍 etc.) are the only emoji — they signal section type, not energy.

9. **Length: aim for 80–120 lines per build step.** Less is under-spec'd. More means you're dumping context that should live elsewhere (in the blueprint stages, not here).

10. **Every step MUST end with a stop-and-review gate.** The gate is what makes this a playbook and not a wishlist.

## Cross-stage anchors (use these consistently)

When the playbook references prior stages, use these exact patterns:

- "From blueprint stage 01 — your wedge is <wedge>"
- "From blueprint stage 04 — service `<Service Name>` owns <entities>"
- "From blueprint stage 05 — feature `F-XX <Title>` flow"
- "From blueprint stage 06 — design system tokens (color `var(--brand)`, spacing scale 4/8/12/16/24)"

These anchors prove the playbook is project-specific. They also let the reader jump back to context when a step is unclear.

## Anti-patterns the playbook MUST avoid

- ❌ Paste-ready "prompts" addressed to an AI tool. The playbook is for a *human* (or AI agent) to follow, not for a chat input field.
- ❌ Generic checklists ("write tests", "deploy to prod"). Every item must be specific to this project.
- ❌ Optional steps. If a step is optional, it does not belong in the playbook. Move it to a "Future expansions" appendix at the bottom.
- ❌ Vague success criteria ("works well", "good performance"). Every gate is a test that passes or fails.
- ❌ Missing dependency arrows. If step N can be done before step M, the dependency tree is wrong — re-sequence.
- ❌ Hyped framing ("amazing!", "incredible!", "🚀🚀🚀"). Senior engineers do not speak this way.

## Reference for tone (read this before writing)

The playbook should read like a *senior engineer's runbook for a high-stakes deploy*. Examples of the right register:

✅ "Auth helpers live in `src/lib/auth/`. Never inline auth checks inside route handlers — that path leads to inconsistent session validation and a CVE waiting to happen."

❌ "Set up authentication! 🔐 NextAuth is great for this — let's get you started!"

✅ "Stop-and-review: Sign up with three different emails. Log out. Log in. Verify session cookie is HttpOnly + SameSite=Lax + Secure (in prod). If any of these is missing, you have a security hole — fix before Step 05."

❌ "Make sure everything works before moving on! 👍"

The playbook is the user's senior reviewer. It treats them as an adult engineer who is going to ship a real product to real users.
