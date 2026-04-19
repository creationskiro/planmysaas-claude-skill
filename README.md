# PlanMySaaS — Claude Skill

> Turn a one-line SaaS idea into a complete blueprint, right inside Claude Code.

```bash
$ /planmysaas "AI tutor for JEE students, voice-first, ₹99/month"

✓ Blueprint generated for: AI tutor for JEE students…

  ./planmysaas-blueprint/
  ├── 01-idea.md            ← Refined idea + audience + business model
  ├── 02-research.md        ← Competitors, problems, opportunities
  ├── 03-analysis.md        ← BMC, SWOT, positioning, PMF score
  ├── 04-architecture.md    ← Services, data models, API surface
  ├── 05-features.md        ← Feature specs with user flows
  ├── 06-frontend.md        ← Routes, wireframes, component tree
  ├── 07-phases.md          ← Release plan + milestones
  ├── 08-build-prompts.md   ← Ready-to-paste prompts for Cursor / Claude Code
  └── README.md             ← Index of everything
```

## Install

```bash
git clone https://github.com/<your-org>/planmysaas-claude-skill ~/.claude/skills/planmysaas
```

That's it. Restart Claude Code — the skill will auto-discover.

## Use

In Claude Code or Claude.ai:

```
/planmysaas "your one-line saas idea"
```

Or just describe a product idea and ask: *"plan this saas for me"* / *"give me a blueprint for this"* — Claude will pick up the skill automatically.

## What gets generated

8 markdown files + index README, all in `./planmysaas-blueprint/` in your current working directory. Each stage is a deep, structured document — competitor analysis, PMF score, full BMC, system architecture, feature specs with acceptance criteria, frontend routes + wireframes, phased release plan, and a Cursor-ready prompt pack.

**Total time:** ~2-3 minutes (depends on Claude tier + your hardware).

## What this is

A **prompt-based** Claude Skill — runs entirely on your Claude tokens, no PlanMySaaS account needed, no API key, no internet round-trips after install. Pure markdown + Claude's reasoning.

## What this isn't (yet)

The **dashboard version at [planmysaas.com](https://planmysaas.com)** has:
- 14 sections (vs 8 here)
- Live recharts (bar charts, BMC grid, architecture canvas)
- Version history + diff view per stage
- Auto-research on real competitor data (web search)
- Re-run any stage with founder feedback
- Team collaboration
- Exports (PDF, JSON, ZIP, share links)
- 9 seed runbooks for ops (refunds, password reset, etc.)

If you want any of those, sign up at [planmysaas.com](https://planmysaas.com) — 100 free credits, no card required.

## Customise

Edit the prompts in `~/.claude/skills/planmysaas/pipeline/` to match your style — they're plain markdown. Common tweaks:

- Change default tech stack in `04-architecture.md`
- Add more sections to a stage
- Tighten the tone in any prompt's "Tone" section
- Add your own stage between existing ones (just renumber)

## License

MIT. Fork it, ship it, share it.

## Credits

Built by [@abhiverma](https://x.com/abhiverma) · powered by Claude Skills · part of the [PlanMySaaS](https://planmysaas.com) ecosystem.
