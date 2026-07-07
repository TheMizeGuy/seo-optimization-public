---
name: seo-optimization
description: "Use when doing any SEO work on any website — auditing or improving Google rankings, organic traffic, or search visibility; keyword research and non-branded query targeting (rank for what the site does); writing or reviewing titles, meta descriptions, headings, or content for search; structured data / JSON-LD; internal linking; Core Web Vitals for search; E-E-A-T or topical authority; backlinks and off-page authority; AI search visibility (AI Overviews, AI Mode, GEO, AEO, ChatGPT, Perplexity); diagnosing traffic drops, penalties, indexing problems, or core-update impact; site migrations; new-site SEO setup; local SEO and Google Business Profile; e-commerce, YMYL, video/image, and international SEO. Also use when tempted to add keywords, schema, or SEO copy to a page — this skill decides whether that is optimization or bloat. Keywords: SEO, rankings, SERP, keyword research, long-tail, query mapping, title tag, sitemap, canonical, crawl, index, CTR, over-optimization."
---

# SEO Optimization — natural ranking, real authority

## Overview

Google ranks the best answer from the most trusted source. Optimization makes that quality
legible to machines; it never substitutes for it. **Over-optimization is penalized harder than
under-optimization**: the March 2024 core update deindexed 837 sites, and every update since has
rewarded first-party "destination" content and demoted optimization theater (May 2026 core:
intermediaries and aggregators lost heavily — major losers −40% to −63% visibility, Sistrix —
while first-party destination sources gained). Google's own May 2026 AI-search
doctrine collapses the new surface into the old rule: "GEO is still SEO". No special markup, no
llms.txt, no chunk-rewriting; the same natural content wins both.

**When in doubt, leave it out.**

## When to use

- Any ranking, organic-traffic, or search-visibility work — audit, implementation, or review
- Writing/reviewing titles, meta descriptions, headings, content, anchors, or schema for search
- Traffic drops, penalty triage, core-update response, migrations, new-site setup
- AI-search visibility (AI Overviews / AI Mode / ChatGPT / Perplexity citations)

**Not for:** paid search, pure social campaigns. Site-specific data-layer skills (a site's own
GSC/GA4 pull workflows) handle their site's data plumbing — pair this skill with them, don't
replace them. **Site-specific policies (brand guardrails, consent
banners, family-friendly rules, "untouchable" surfaces) always override anything here.**

## What actually ranks — allocate effort by weight

| Factor | Weight | Implication |
|---|---|---|
| Consistent satisfying content | 23% | The #1 lever is always the content itself |
| Keywords in title tag | 14% | One accurate title, not a keyword container |
| Backlinks | 13% ↓ | Earned authority; declining weight since 2024 |
| Niche expertise (topical authority) | 13% | Depth before breadth; clusters, not scattered posts |
| Searcher engagement | 12% ↑ | NavBoost counts clicks, dwell, pogo-sticking |
| Content freshness | 6% | Annual updates average +4.6 positions |
| Everything else (schema, URL keywords, header keywords…) | ~1% each | Hygiene, never strategy |

(First Page Sage Q1 2025 — still the operative study; no 2026 refresh exists as of 2026-07.)

Confirmed internal signals worth acting on (2024 API leak + DOJ trial): **NavBoost** (good/bad
clicks, last-longest-click, 13-month window): satisfy intent so users don't bounce back to the
SERP. **siteAuthority** (domain-level): site-wide quality compounds. **siteFocusScore**:
topical focus beats sprawl. **originality scoring**: don't rephrase competitors.
**titlematchScore**: the title must match the queries you actually target.

## The naturalness gate — every element passes before shipping

**The test: would this element read the same if search engines didn't exist?** If a human editor
with no SEO knowledge would flag it as odd, redundant, or list-like, it fails, regardless of
which "signal" justifies it.

Strong models don't fail this by crude stuffing. They fail it by *systematic mild
over-optimization*: each choice defensible, the sum reading as SEO'd. Baseline testing produced
exactly these patterns; the recipes below are the required shape.

### What natural elements ARE

| Element | Recipe | The smell that fails the gate |
|---|---|---|
| Title tag | ONE primary phrase the way a person says it + one concrete differentiator, brand last, 50-60 chars | Two query phrases joined by "with/&/,": a keyword container — a prime rewrite trigger (Google rewrites roughly a third of titles overall) |
| H1 | States what the page delivers, in the page's own voice | Title-tag keyword set restated |
| Headings | Outline the content from user questions/tasks FIRST, then check which queries it serves | Any heading traceable to a keyword list rather than the outline |
| Body copy | Answers, evidence, specifics a reader needs; entities appear where they serve the sentence | A 4+ item entity/species/brand list justified as "coverage"; word count added as "depth" |
| Meta description | One-sentence pitch of what the reader gets + call to action | Query phrases packed for bolding |
| Anchors | Describe the destination in the sentence's own words | Exact-match anchors chosen to hit a distribution quota |
| Boilerplate (nav, footer, taglines) | Names sections; expresses brand voice | Keywords inserted into nav labels, footer straplines, copyright lines |
| Schema | Marks up what the page visibly IS, real data only | Types added for eligibility; markup diverging from visible content (manual-action category) |
| FAQ | Questions users genuinely ask, answered plainly | Q&A written as "mini landing targets" for PAA capture |

Worked example — one title through the gate:

- FAILS: `Best Hiking Boots 2026 — Waterproof Hiking Boots, Trail Boots & Backpacking Footwear | TrailLab` — three query phrases spliced with "—/&": a keyword container; Google rewrites it, users don't click it.
- PASSES: `Best Hiking Boots of 2026: 14 Pairs Trail-Tested | TrailLab` — one phrase the way a person says it, one concrete differentiator ("14 pairs trail-tested"), brand last, 58 chars.

### Rationalizations — all of these mean STOP

| Rationalization | Reality |
|---|---|
| "Front-load the primary keyword AND cover the secondaries in the title" | That's a container, not a title. Secondaries live in H2s, body, and other pages |
| "Headings are weighted relevance signals — one per target query" | Query-mapped structure is doorway thinking at section scale. Outline from user needs |
| "Modern ranking is entity-based, so list the entities" | Entity stuffing is keyword stuffing in 2026 clothes. Entities serve sentences, not inventories |
| "Sitewide anchors and boilerplate reinforce the topic" | Boilerplate keywords are the oldest stuffing pattern there is |
| "Each FAQ is a mini landing target" | Write what users ask. SERP capture follows genuine questions, not the reverse |
| "More schema types, more eligibility" | Schema-content mismatch is a manual action. FAQ rich results are dead (May 2026); markup for them is cargo cult |
| "300 more words adds depth" | Depth = new answers. Padding raises pogo-sticking, and NavBoost counts it |
| "It's white-hat, so more is better" | The failure mode isn't spam; it's a page that reads SEO'd. That's what engagement signals punish |

### Red flags — self-check before shipping

- A title with "&" or a second joiner splicing query phrases together
- Any heading you generated from the keyword list instead of the content outline
- A sentence listing 4+ entities where 2 do the explanatory job
- Keyword edits to nav labels, footers, taglines, or decorative-image alt text
- Copy you would not keep if Google didn't exist
- Justifying any element by its signal weight instead of its reader value
- Impressions, AI mentions, or long-tail coverage rising while clicks, engaged sessions, branded
  demand, conversions, and citation quality stay flat/down

## Workflow

**0. Validate intent before touching anything.** Check what the live SERP serves for the target
query: page type, format, who ranks. Content type must match the SERP pattern (product pages
rank for product SERPs; a blog post won't). If you can't check the live SERP, say so explicitly
and mark the assumption. Then apply the **destination test**: is this site the natural endpoint
for the query (owns the data, inventory, or expertise), or a layer between the user and the
answer? Two consecutive 2026 core updates moved visibility from intermediaries to first-party
destinations: aggregation-shaped content is structurally at risk regardless of polish, in both
classic ranking and AI citation (evidence and sourcing: `reference/ai-search-geo.md` §4).

**0.5. Run the policy/risk preflight before adding URLs or copy.** If the request asks for
"maximum pages", "GEO hacks", "AI mentions", "programmatic scale", "city pages", "affiliate
roundups", "expired domains", or "parasite/reputation leverage", classify it before optimizing:

| Risk | The question that decides it |
|---|---|
| Scaled content / impression farming | Would these pages exist if they could not earn impressions? |
| AI-response manipulation | Is the page meant to manipulate AI answers rather than help a user complete a task? |
| Doorway/cannibalization | Are variants targeting the same intent with thin substitutions? |
| Site reputation abuse | Is third-party or weakly owned content using the host's authority more than its own value? |
| Thin affiliation | Is there first-hand testing, comparison, pricing/context, or decision help beyond merchant copy? |
| Expired-domain abuse | Is authority being borrowed from an unrelated prior domain purpose? |

Any "yes" moves the work to `reference/anti-patterns.md` before implementation. The compliant
path is fewer stronger pages with original evidence, clear ownership, crawlable structure, and a
measurable user/business purpose.

**1. Audit before optimizing** (existing sites) — `reference/measurement-and-audit.md`. For a
deployed site, the proven full-audit shape is three parallel read-only agents that triangulate:
SERP/competitor/intent + in-repo technical (file:line evidence) + deployed crawlability
(rendered HTML, ~30 URLs, Googlebot UA). Never audit only the repo — audit what Google sees.
Execution mode: these agents inherit the session model — always the strongest available Claude.
If the session model is already top-tier and the site is small, run the three lenses inline in
the main context instead of dispatching separate agents; never block on, or wait for, a specific
model. Keep each lens read-only, dispatched or inline. Per-lens deliverable shapes and
acceptance criteria are specified in `reference/measurement-and-audit.md` — check results
against them before synthesizing.

Minimum evidence floor before any recommendation, audit or not: (1) live SERP for 2-3 target
queries, (2) rendered HTML of the key pages via Googlebot UA, (3) GSC 28-day data when
accessible. Prefer live instruments per the evidence toolchain in
`reference/measurement-and-audit.md`, and label anything second-hand. Classify every GSC-sourced
finding LIVE-DEFECT / ALREADY-FIXED / INTENDED before it enters the work list: GSC reports
Google's last crawl, which can trail your deploys by weeks.

**2. Prioritize by weight × effort.** P0 = anything blocking crawl/index (robots, noindex,
broken canonicals); fix immediately. Then work the weight table top-down: content completeness
before title polish before schema hygiene. Do not spend equal effort on 1%-weight items.

**3. Implement through the naturalness gate.** Recipes above; depth per element in
`reference/`. New public routes ship with sitemap entries in the same change.

**4. Verify — do not claim done until each of these holds:**

- Rendered HTML fetched with a Googlebot UA (not view-source) shows the intended
  title/meta/canonical/robots/H1 and JSON-LD on every changed URL.
- Every changed schema block passes the Rich Results Test with zero errors — structured data
  that fails validation is worse than none.
- New/changed public routes appear in the sitemap in the same change; GSC URL inspection run
  and indexing requested.
- The red-flags self-check (above) re-run against the final diff comes back clean.
- Post-deploy: rendered-HTML check repeated on production, not assumed from staging.

## The honesty rule

Most "why aren't we on page 1" cases decompose to roughly **70% off-site** (brand authority,
backlinks, ecosystem presence) **+ 30% content keyword leadership**; technical SEO is usually
already adequate (proven in production, 2026-05). State this split in every diagnosis instead of
inventing on-site work to look busy. Set honest timelines: algorithmic recovery 6–24 months,
authority building 6–12 months, content clusters 3–6 months to +40% traffic. A deliverable that
promises head-term rankings from on-page tweaks alone is wrong.

The split is a diagnosis of HEAD-term gaps, never a reason to skip non-branded demand capture:
authority sets the ceiling, query coverage fills everything under it, and mid/long-tail function
queries are winnable at current authority while the brand work compounds
(`reference/keyword-strategy.md`, the authority-relative ladder). A rising branded line with a
flat non-branded line means the site is found only by people who already know it — that is the
gap this skill exists to close, worked in both lanes at once.

## Decision trees

```
New site, no SEO?          -> measurement-and-audit (launch checklist) -> technical-seo -> on-page-and-content
Traffic dropped?           -> measurement-and-audit (traffic-drop triage runbook) -> anti-patterns (penalty recovery)
Not indexed / GSC 404s or coverage errors? -> measurement-and-audit (GSC lag discipline: LIVE-DEFECT / ALREADY-FIXED / INTENDED) -> technical-seo (indexing signals, status codes)
Bad CTR at stable positions? -> measurement-and-audit (CTR quick-win loop) -> on-page-and-content (title/meta recipes)
Overtake a specific competitor? -> authority-and-offpage (five-gap framework) -> keyword-strategy (gap queries)
How often to publish/update? -> on-page-and-content (publishing cadence, freshness/decay)
Rank for what the site does? (non-branded) -> keyword-strategy (function-query coverage, query→page map) -> on-page-and-content
Building a content program?-> keyword-strategy (map first) -> on-page-and-content (clusters, E-E-A-T) -> authority-and-offpage (entity)
Not ranking despite clean tech? -> authority-and-offpage + the honesty rule + keyword-strategy (the winnable middle)
AI visibility?             -> ai-search-geo -> structured-data (entity graph) -> on-page-and-content
Schema work?               -> structured-data (mirror-visible-content rules first)
Local / intl / video / image / news / e-commerce / migration / YMYL? -> specialized
Tempted to add keywords/schema/SEO copy? -> the naturalness gate, then decide
```

## Common mistakes

| Mistake | Consequence |
|---|---|
| Lazy-loading the LCP image | The most common self-inflicted CWV regression |
| FAQ/schema JSON-LD drifting from visible text | Structured-data spam signal; manual-action category |
| `aggregateRating` without real collected ratings | Manual action strips ALL rich results site-wide |
| noindex/robots block left on after staging or migration | Silent deindexing; check first in every audit |
| Optimizing titles for keywords at the cost of click-appeal | NavBoost measures clicks; a keyword title nobody clicks loses twice |
| New page per query variant | Cannibalization — consolidate, 301 the loser |
| Growing impressions without clicks/engagement/conversions | Impression farming — stop expansion and improve intent satisfaction |
| Panic-editing during a core-update rollout | Noise that masks what actually moved; wait for rollout completion |
| Fixing stale GSC findings without live verification | Phantom-fix churn: in one production audit, 8 of 9 GSC-bucket findings were already fixed or intended. Classify LIVE-DEFECT / ALREADY-FIXED / INTENDED first |
| Trusting SEO-tool metrics uncritically | "Engagement Reliability" (2026) is a fabricated CWV metric circulating in content mills. Verify against Google primary sources |

## Reference map

| File | Contents | Load when |
|---|---|---|
| `reference/on-page-and-content.md` | Titles, meta, headings, intent, internal links, images, E-E-A-T, YMYL requirements, clusters, freshness/decay, publishing cadence, content workflow | Writing or reviewing any page/content |
| `reference/keyword-strategy.md` | Non-branded demand capture: function-query coverage, query→page map, research pipeline, KD ladder, low-volume reality, non-branded measurement | Choosing what to rank for; "we only rank for our name" |
| `reference/technical-seo.md` | Crawl/index, sitemaps, canonicals, CWV fixes, JS SEO, status codes, server config | Technical work or audits |
| `reference/structured-data.md` | JSON-LD doctrine, type selection, @id entity graph, deprecations, validation, snippets/PAA/Discover | Any schema work |
| `reference/authority-and-offpage.md` | Link quality, disavow, brand signals, entity SEO/Knowledge Graph, digital PR, competitor gaps | Authority strategy; "why aren't we ranking" |
| `reference/ai-search-geo.md` | AI Overviews/AI Mode state, evidence-backed GEO, llms.txt verdict, AI crawlers, AI-traffic measurement | AI-search questions |
| `reference/measurement-and-audit.md` | GSC/GA4, KPIs, live evidence toolchain, GSC lag discipline, traffic-drop triage runbook, audit methodology + 3-agent pattern, launch checklist, cadence, update response | Audits, reporting, monitoring, traffic drops |
| `reference/anti-patterns.md` | The full over-optimization catalog: crude spam AND the subtle 2026 class, detection heuristics, recovery | Before shipping; penalty triage |
| `reference/specialized.md` | Local, mobile/intl, video/image, news/publisher, e-commerce, platform gotchas, migration, accessibility, YMYL | Situation-specific rules |
