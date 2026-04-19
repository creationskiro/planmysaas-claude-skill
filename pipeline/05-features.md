# Stage 5 — Feature specifications

Generate `./planmysaas-blueprint/05-features.md`. Read prior stages.

## Output structure

```markdown
# Feature specifications — <Project name>

## Summary
- Total features: <N>
- Modules covered: <M>
- Coverage: 100% of modules have at least 1 feature spec

## Feature index

| ID    | Module                    | Title                              | Priority | Effort |
|-------|---------------------------|------------------------------------|----------|--------|
| F-01  | Identity                  | User Registration & Login          | P0       | 2 days |
| F-02  | Identity                  | Role-Based Access Control          | P0       | 1 day  |
| ...   |                           |                                    |          |        |

Sort by priority (P0 → P3), then by ID.

## Feature specs (12-20 features)

For EACH feature, render this full block:

---

### F-XX · <Feature title>

**Module:** <module name>
**Primary actor:** <persona> · **Secondary:** <persona>
**Priority:** P0 / P1 / P2 / P3 · **Effort:** <X days>

#### Purpose
1-2 sentences. Why this exists. Which problem-cluster from research it solves.

#### User flow
Numbered steps from actor's POV (5-9 steps). Include happy path + 1 alternate path.

```
1. User opens /courses page
2. System loads course list (cached if available)
3. User filters by topic
4. User clicks a course card
5. System shows course detail with syllabus
6. User clicks "Enroll"
7. If not logged in → redirect to /login → return here
8. System creates Enrollment record
9. User lands on /learn/<course-id>
```

#### Acceptance criteria
Bulleted checklist (5-8 items). Each must be testable.

- [ ] User can filter courses by topic, level, price
- [ ] Filter state persists in URL (shareable)
- [ ] Course list loads in <500ms p95
- [ ] Enrollment is idempotent (clicking twice doesn't create duplicates)
- [ ] Logged-out user is redirected, then returned to course detail after login

#### Edge cases
3-5 bullets. Empty states, race conditions, validation failures.

#### Telemetry events
2-4 events to fire (e.g. `course_viewed`, `enrollment_started`, `enrollment_completed`).

---

(Repeat for each feature.)
```

## Quality rules

- Every feature must map to a **module** from the architecture stage.
- Every P0 feature must have a clear path to revenue or core retention.
- Acceptance criteria use the past tense or "User can…" form. Never "should be able to".
- Effort estimates: 1-3 days for simple, 3-7 for medium, 7-14 for hard. If something feels >14 days, split it.
- 12-20 features total. Less = under-spec'd. More = unfocused — push the rest to a Backlog section at the end.

## Tone

PM writing for engineers. Tight, testable, specific. No marketing language.
