# Contributing to PlanMySaaS Claude Skill

Forks, PRs, and issues all welcome. The skill is plain markdown — no build step, no compile step, no package.json, no JavaScript. Editing a prompt file and seeing the change is one save away.

## Ways to contribute

### 1. Improve a stage prompt

Open any file in `pipeline/` and rewrite it. Better prompts produce better blueprints. Run your fork on a few different SaaS ideas before opening the PR — paste the inputs you tested with into the PR description so reviewers can verify.

Especially valuable:
- **Sharper acceptance criteria** in stage 5 (features) and stage 8 (build playbook)
- **Better cross-stage anchors** — the playbook is most useful when each step references concrete IDs from earlier stages
- **Domain-specific defaults** — if you build a lot of marketplace SaaS, B2B SaaS, AI tools, mobile-first products, etc., the architecture stage benefits from your opinionated defaults

### 2. Add a stage variant

Drop a new file like `pipeline/05b-mobile-features.md` for a mobile-first variant of stage 5. Or `pipeline/09-marketing.md` for an extra marketing-plan stage. Then update `SKILL.md` to reference it. The skill is composable — variants ship cheap.

### 3. Add a sibling skill

Have an idea for `/planmysaas-mvp` (a 4-stage faster cut), `/planmysaas-validate` (idea validation only), `/planmysaas-redesign` (replan an existing product)? Open an issue first to discuss, then ship it as a parallel folder under `~/.claude/skills/`. We can list community sibling skills in the README.

### 4. Localise

Hindi, Spanish, French, Portuguese — the prompts are plain English markdown. Translate any pipeline file and add a language note at the top. Submit as `pipeline/01-idea-refine.es.md` etc. Open an issue first so we can coordinate which prompts get translated and in what order.

### 5. Bug fixes

If Claude misinterprets a stage instruction, generates generic content, or hits an edge case, open an issue with:
- The exact input idea you used
- The output you got
- The output you expected
- (Helpful) Screenshots or full markdown of the generated file

## How to open a good PR

1. **Fork** this repo to your GitHub account
2. **Create a branch** named `<type>/<short-description>` — e.g. `feat/mobile-stage-variant` or `fix/architecture-tech-stack-defaults`
3. **Make the change** — edit prompts, save, commit
4. **Test locally** — install your fork to `~/.claude/skills/planmysaas-test/`, run `/planmysaas-test "<test idea>"`, verify the output
5. **Open the PR** with:
   - What changed and why
   - The test input(s) you tried
   - A short snippet of the generated output (so reviewers can compare against current behavior)

PRs that include before/after output samples merge fastest.

## What we will NOT merge

- **Tool-specific prompts** — the skill is intentionally tool-agnostic at the build step. Prompts that hard-code a specific editor or paid service get rejected.
- **Marketing copy** — the prompts produce blueprints for engineers, not pitch decks. No "amazing!", no exclamation marks, no emoji-heavy tone outside the documented section markers (🎯 📍 ✅ etc.).
- **Vendor lock-in** — defaults like Next.js + Postgres are opinionated but replaceable. PRs that hard-couple to a paid SaaS without a clear opt-out get rejected.
- **AI-generated PRs without testing** — every PR must show evidence that the contributor actually ran the change against a real input.

## Code of Conduct

This project adopts the [Contributor Covenant](CODE_OF_CONDUCT.md). By participating, you agree to abide by its terms.

## License

By contributing, you agree that your contributions will be licensed under the MIT License — same as the rest of the project.

## Thank you

Every PR — even a typo fix — makes the skill better for the next solo founder who installs it. Ship it, however small.
