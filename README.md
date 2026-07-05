# seo-optimization

A site-agnostic SEO playbook skill for [Claude Code](https://claude.ai/claude-code): real
authority, higher Google rankings, zero keyword stuffing or over-optimization bloat. Current as
of July 2026, primary-sourced (Google Search Central, Search Status Dashboard, web.dev, official
crawler docs), and behaviorally tested against the failure mode that actually matters — capable
models over-optimizing subtly, not crudely.

**Version 1.1.0** · MIT · one skill, ten reference files, no dependencies

## Install

### As a plugin (recommended — updates via `claude plugin update`)

```bash
claude plugin marketplace add TheMizeGuy/seo-optimization-public
claude plugin install seo-optimization@seo-optimization
```

Update later with `claude plugin update seo-optimization@seo-optimization`. Running sessions
pick up updates after `/reload-plugins`; new sessions load the current version automatically.

### As a bare user skill (no plugin system)

```bash
git clone https://github.com/TheMizeGuy/seo-optimization-public.git
ln -s "$(pwd)/seo-optimization-public/skills/seo-optimization" ~/.claude/skills/seo-optimization
```

Updates arrive when you `git pull`. Use one install method, not both — installing the plugin
AND symlinking the skill loads it twice.

## Using it

No commands to learn. The skill auto-triggers on SEO-shaped requests — rankings, keyword
research, titles/meta, structured data, traffic drops, indexing problems, AI-search visibility,
migrations, local/e-commerce/YMYL work. Ask naturally:

```text
Why did our organic traffic drop 30% this month?
We rank #1 for our brand name and nowhere for anything else. Fix that.
Do an SEO audit of https://example.com
Should we add FAQ schema to these pages?
How do we show up in ChatGPT answers and AI Overviews?
Review this page's title and meta description.
We're migrating domains next month — what's the SEO protocol?
```

**[USAGE.md](USAGE.md) is the full use guide** — worked walkthroughs (deployed-site audit,
non-branded demand capture, traffic-drop triage), what to expect from each workflow, and a
troubleshooting table.

## What's inside

- **The naturalness gate** — every element must read the same as it would if search engines
  didn't exist. Recipes for what natural titles, headings, anchors, and schema ARE, a
  rationalization table for the tempting-but-wrong moves, and a red-flags self-check.
- **Ranking-weight-ordered workflow** — live SERP/intent validation and the destination test
  first, a policy/risk preflight (scaled content, AI-response manipulation, doorways), audit
  before optimizing, and verification via rendered Googlebot-UA captures.
- **Non-branded demand capture** — function-query coverage (rank for what the site *does*),
  the query→page map, an authority-relative prioritization ladder, honest zero-volume handling,
  and the non-branded scoreboard.
- **Operational runbooks** — seven-step traffic-drop triage, GSC lag discipline (classify every
  finding LIVE-DEFECT / ALREADY-FIXED / INTENDED before fixing), monthly CTR quick-win loop,
  core-update response, migration protocol, new-site launch checklist.
- **AI search / GEO, evidence-graded** — the July 2026 state of AI Overviews and AI Mode, what
  actually earns citations (sourced), the llms.txt verdict, the three-tier AI crawler map, AI
  traffic measurement, and a superseded-claims ledger so stale numbers don't get repeated.
- **The honesty rule** — most "why aren't we page 1" cases are majority off-site authority; the
  skill says so instead of selling on-page busywork, then works the winnable middle anyway.

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

## Releases

Versioned releases on the [Releases page](https://github.com/TheMizeGuy/seo-optimization-public/releases);
change history in [CHANGELOG.md](CHANGELOG.md). The knowledge layer is dated throughout — every
volatile claim carries its source and date, and superseded numbers move to an explicit ledger
rather than being silently overwritten.
