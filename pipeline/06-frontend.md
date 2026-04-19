# Stage 6 — Frontend blueprint

Generate `./planmysaas-blueprint/06-frontend.md`. Read prior stages, especially features.

## Output structure

```markdown
# Frontend blueprint — <Project name>

## Routes (sitemap)

Group by section. For each route: path · purpose · auth required · which feature(s) it serves.

```
PUBLIC
  /                       Landing page                                  no
  /pricing                Pricing                                       no
  /login                  Login                                         no
  /signup                 Signup with email + Google OAuth              no

APP (auth required)
  /app                    Dashboard                                     yes
  /app/courses            Browse course catalog                         yes  F-01, F-04
  /app/courses/[id]       Course detail                                 yes  F-04
  /app/learn/[courseId]   Lesson player + progress                      yes  F-05
  /app/quizzes/[id]       Take a quiz                                   yes  F-07
  /app/dashboard          Personal progress dashboard                   yes  F-12

ADMIN (admin role)
  /admin                  Admin home                                    yes
  /admin/users            User management                               yes
  /admin/content          Course / lesson editor                        yes
```

## Page specs (top 8 routes)

For each major page:

### /<route>

- **Hero / above-fold**: 1 sentence describing what the user sees first
- **Sections** (top to bottom): list of 4-8 sections with 1-line description each
- **Components used**: list of 5-10 component names from the component tree below
- **Data fetched**: which API endpoints this page calls
- **Empty state**: what shows when there's no data
- **Loading state**: skeleton / spinner / streaming
- **Error state**: how errors are surfaced

## Wireframes (text-form)

For each major page, ASCII wireframe:

```
/app/courses
┌─────────────────────────────────────────────────┐
│  [Logo]  Browse  Learn  Pricing      [Avatar]  │
├─────────────────────────────────────────────────┤
│                                                 │
│  Browse courses                  [+ Suggest]    │
│  ───────────                                    │
│                                                 │
│  [All] [AI] [Robotics] [Live]   🔍 Search      │
│                                                 │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐           │
│  │ Course  │ │ Course  │ │ Course  │           │
│  │ card    │ │ card    │ │ card    │           │
│  └─────────┘ └─────────┘ └─────────┘           │
│                                                 │
│  Showing 12 of 47 · Load more                   │
└─────────────────────────────────────────────────┘
```

## Component tree (12-25 reusable components)

Group by category:

**Layout**
- `<Navbar>`, `<Sidebar>`, `<Footer>`, `<PageHeader>`

**Form**
- `<TextInput>`, `<Select>`, `<DatePicker>`, `<FileUpload>`, `<FormError>`

**Data display**
- `<DataTable>`, `<EmptyState>`, `<Stat>`, `<ProgressBar>`, `<Badge>`

**Domain**
- `<CourseCard>`, `<LessonPlayer>`, `<QuizQuestion>`, `<EnrollmentButton>`

For each: 1-line purpose + key props (3-5).

## Design system

- **Colors**: brand primary, neutral scale (5 stops), semantic (success/warn/error/info)
- **Typography**: H1-H4 sizes + body + caption + mono. Recommend Inter / Inter Tight / JetBrains Mono.
- **Spacing scale**: 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 (tight → loose)
- **Radius**: 4 / 8 / 12 / 16 (cards / buttons / chips)
- **Shadow**: 3 levels (subtle / medium / dramatic)
- **Motion**: cubic-bezier(.2,.7,.2,1) for entry, 0.2-0.4s default

## Responsive grid

- Mobile (≤640): single column, stack everything
- Tablet (641-1024): 2-column where natural
- Desktop (≥1025): max-width 1280px, sidebar at 1280+
```

## Quality rules

- Routes must follow **RSC patterns** (server components by default, client only when interactive).
- Every page must have **explicit empty / loading / error states** named.
- Component names use PascalCase + describe domain (`<CourseCard>` not `<Card>`).
- Wireframes show what the user actually sees — no marketing copy, just structure.

## Tone

Senior frontend lead handing off to a junior team. Concrete components, opinionated defaults.
