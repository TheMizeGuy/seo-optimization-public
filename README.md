# seo-optimization

A site-agnostic SEO playbook skill for [Claude Code](https://claude.ai/claude-code): real
authority, higher Google rankings, zero keyword stuffing or over-optimization bloat. Current as
of July 2026, primary-sourced (Google Search Central, Search Status Dashboard, web.dev, official
crawler docs), and behaviorally tested against the failure mode that actually matters — capable
models over-optimizing subtly, not crudely.

**Version 1.0.0** · MIT · single skill, no dependencies

## Install

```bash
git clone https://github.com/TheMizeGuy/seo-optimization-public.git
ln -s "$(pwd)/seo-optimization-public/skills/seo-optimization" ~/.claude/skills/seo-optimization
```

The skill auto-triggers on SEO-shaped requests (rankings, keyword research, titles/meta, schema,
traffic drops, indexing problems, AI-search visibility, migrations, local/e-commerce/YMYL work).

## What it does

- **The naturalness gate** — every element must read the same as it would if search engines
  didn't exist; recipes for what natural titles, headings, anchors, and schema ARE, plus the
  rationalization table for what to refuse.
- **Ranking-weight-ordered workflow** — intent/SERP validation and the destination test first,
  policy/risk preflight, audit before optimizing, verify with rendered Googlebot-UA captures.
- **Non-branded demand capture** — function-query coverage, the query→page map, an
  authority-relative prioritization ladder, honest zero-volume handling.
- **Operational runbooks** — traffic-drop triage, GSC lag discipline (classify findings
  LIVE-DEFECT / ALREADY-FIXED / INTENDED before fixing), CTR quick-win loop, core-update
  response, migration protocol, launch checklist.
- **AI search / GEO, evidence-graded** — July 2026 state of AI Overviews/AI Mode, what earns
  citations (with sources), the llms.txt verdict, the AI crawler map, and a superseded-claims
  ledger so stale numbers don't get repeated.
- **The honesty rule** — most "why aren't we page 1" cases are majority off-site authority;
  the skill says so instead of selling on-page busywork, then works the winnable middle anyway.

## Layout

| Path | Contents |
|---|---|
| `skills/seo-optimization/SKILL.md` | Doctrine, naturalness gate, workflow, decision trees, reference map |
| `reference/on-page-and-content.md` | Titles, meta, headings, E-E-A-T, clusters, freshness, pruning |
| `reference/keyword-strategy.md` | Non-branded demand capture, query→page map, research pipeline |
| `reference/technical-seo.md` | Crawl/index, sitemaps, canonicals, CWV, JS SEO, server config |
| `reference/structured-data.md` | JSON-LD doctrine, @id entity graph, retired-feature traps |
| `reference/authority-and-offpage.md` | Link quality, digital PR, entity SEO, brand-SERP audit |
| `reference/ai-search-geo.md` | AI Overviews/AI Mode/GEO, crawler map, AI-traffic measurement |
| `reference/measurement-and-audit.md` | GSC/GA4, evidence toolchain, runbooks, audit methodology |
| `reference/anti-patterns.md` | The over-optimization catalog + detection heuristics + recovery |
| `reference/specialized.md` | Local, international, video/image, news, e-commerce, migration, YMYL |

Figures labeled "internal benchmark" come from the maintainer's private reference corpus and are
directional; primary-sourced claims carry their source and date inline.

## Doctrine (short form)

1. Content quality and topical authority outrank every trick.
2. Natural language over keyword density — Google uses semantic understanding, not counting.
3. Over-optimization is penalized harder than under-optimization. When in doubt, leave it out.
4. Authority sets the ceiling; query coverage fills everything under it — work both lanes.
