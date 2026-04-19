# Stage 2 — Market research

Generate `./planmysaas-blueprint/02-research.md`. Read `01-idea.md` first to scope the search.

## Output structure

```markdown
# Market research — <Project name>

## Competitors (5-8)

For each competitor: name · category · 2-line description · top 3 strengths · top 3 weaknesses · opportunity score (1-10).

Categories:
- **Direct** — same audience, same job
- **Adjacent** — solves part of it
- **Substitute** — DIY workaround (YouTube, ChatGPT, spreadsheet)
- **Manual alternative** — what people do without any tool

End with: 1-row table sorted by opportunity score, columns = name / type / key weakness / score.

## Problem clusters (top 5)

Group recurring user complaints into themes. For each:
- **Theme name**
- **Frequency** (how often this comes up — qualitative)
- **Severity** (low/med/high)
- **Example phrasings** (3 real quotes / paraphrases users would say)

## Market gaps (top 5)

What no competitor does well. For each: gap statement · opportunity hypothesis · who would care.

## Insights (top 5)

Non-obvious things that change strategy. Each insight has: statement · reasoning · what it implies for the product.

## Strategic direction

3-paragraph recommendation:
1. **Best wedge** — narrowest, fastest path to first 100 paying users
2. **Initial positioning** — exact phrasing
3. **Core product promise** — the one sentence the audience would repeat to a friend

## Build first / Don't overbuild / Delay to later

Three columns of 4-6 items each. The "delay" column matters most — it prevents scope creep.
```

## Quality rules

- Competitors must be REAL companies (Coursera, Notion, ChatGPT, etc.). If domain is too niche, include manual alternatives + adjacent tools.
- Don't fabricate market size numbers. Say "directional" or omit.
- Opportunity scores: high = weak competitor + strong gap. Justify in one phrase per competitor.
- Insights should be the kind a founder hasn't thought of (3 of 5 should surprise them).

## Tone

Analytical. Data-shaped. Read like a McKinsey one-pager, not a blog post.
