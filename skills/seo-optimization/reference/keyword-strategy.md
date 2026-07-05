# Keyword Strategy and Demand Capture

Purpose: how a site earns non-branded rankings: the queries people type when they need what the
site DOES and don't know it exists. This file owns query research, the function-query coverage
method, the query→page map, prioritization, and low-volume reality. Placement recipes stay in
on-page-and-content.md; the naturalness gate stays in SKILL.md and applies to everything here.

## The balance doctrine — authority sets the ceiling, coverage fills it

The honesty rule (~70% off-site / ~30% content keyword leadership) explains why a site isn't
page 1 for HEAD terms. It is not a reason to skip non-branded targeting; misreading it that way
leaves the entire winnable middle on the table:

| Lever | What it controls | Time horizon |
|---|---|---|
| Brand/entity authority | The ceiling: which difficulty tier of queries you can win at all | 6-12+ months, partly outside your hands |
| Query coverage (this file) | How much of the demand UNDER that ceiling you actually capture | Weeks to months, fully in your hands |

70% of search traffic is long-tail. A site with modest authority that systematically owns its
function queries at KD 0-29 outperforms a site waiting for authority before targeting anything.
Work both lanes: authority building per authority-and-offpage.md, demand capture per this file,
reported separately (branded growth measures marketing; non-branded growth measures SEO
discovery).

## Function-query coverage — rank for what the site does

The highest-yield non-branded queries are the ones that describe the site's functions. Method:

1. **Enumerate capabilities.** List every task a user can complete and every dataset, tool,
   calculator, comparison, or inventory the site exposes. Be literal: "look up X prices",
   "convert A to B", "check whether Y is compatible with Z", "browse N by category".
2. **Derive the query set per capability.** For each function, write the queries someone types
   when they need it and have never heard of the site. Cover the phrasings: task ("how to check
   X"), object ("X checker", "X calculator", "X database", "X prices"), problem ("X not
   working", "is X worth it"), and comparison ("X vs Y", "best X for Z"). This is user-language
   work, not tool work; do it first, then validate with tools.
3. **Validate and expand with evidence.** GSC queries already earning impressions (positions
   4-20 are striking distance; up to ~30 still signals demonstrated demand worth mapping);
   autocomplete and People Also Ask chains; internal
   site-search logs (the literal phrasing of users already on the site); community phrasing
   (Reddit, forums, Discord: how real people name the task); competitor keyword gap
   (authority-and-offpage.md five-gap framework).
4. **Check coverage.** For every query cluster: does a page exist that owns it? Does that page's
   type match the live SERP (workflow step 0)? Does it currently rank, and where? The output is
   the query→page map below, with a gap list.
5. **Close gaps by the map, not by volume.** A missing page for a function the site genuinely
   serves is a build; a weak page is an upgrade; two pages splitting one intent is a
   consolidation + 301. Every new URL enters the map before it enters the sitemap.

Guardrail: this method generates pages the site has standing to own — pages that pass the
destination test and the preflight. It never authorizes fan-out variants; one intent, one page.
When a function's query set is inherently large (a lookup page per item, location, or entity in
a real dataset), that is programmatic-SEO territory: the uniqueness test and staged batch gates
in authority-and-offpage.md govern it, and the site's own data is exactly what makes those pages
destination content rather than doorways.

## The query→page map — the standing artifact

Every target query cluster is owned by exactly one page, and every indexable money page owns
exactly one primary cluster. Maintain the map as a table in the repo/CMS; it is the
cannibalization firewall and the content plan in one artifact.

| Column | Content |
|---|---|
| Cluster | Primary query + variants (SERP-overlap clustered: 3+ shared ranking URLs = same cluster) |
| Intent | Informational / commercial / transactional / navigational, from the live SERP |
| Owning URL | Exactly one; blank = gap to build |
| SERP shape | Dominant page type + features present (AIO, snippet, video…) |
| Position | Current, from GSC, refreshed on cadence |
| Status | build / upgrade / consolidate / holding |

Rules: a new page ships only with a map row (no row, no URL); two rows sharing an owning URL
means the clusters merged; two URLs claiming one cluster means consolidate + 301 (positions 5-15
split is the classic symptom; on-page-and-content.md cannibalization detection).

## Research methodology (full pipeline)

Process: seed discovery (GSC existing queries + function enumeration above + competitors) →
expansion (questions, modifiers, autocomplete, PAA) → intent classification
(informational/commercial/transactional/navigational) → difficulty check → clustering →
prioritization (below) → content mapping into the query→page map → gap analysis.

### KD validation

**KD scores vary 20-30% between tools** — always validate with manual SERP review (who ranks,
their authority, content quality, backlinks). Pages targeting **KD < 30 are 3.5x more likely to
rank top 10 within 6 months** (internal-benchmark figure).

| KD | Reality |
|---|---|
| 0-14 | Often accurate; thin competition |
| 15-29 | Achievable within 6 months for a new domain |
| 30-49 | Needs established authority + good content |
| 50-69 | Significant authority + links + excellent content |
| 70-100 | Major brands / Wikipedia territory; near-impossible for new entrants |

### Clustering and volume

- SERP-overlap clustering: **3+ shared ranking URLs between two keywords = same cluster** (one page targets both)
- **70% of all search traffic comes from long-tail keywords** — don't chase only head terms
- Volume accuracy: Keyword Planner gives ranges and groups similar terms; Semrush/Ahrefs clickstream-derived at ±20-30%; **GSC actual data is most accurate for queries you already rank for**; Trends is relative-only (seasonality)

### Per-keyword SERP analysis checklist

- [ ] Dominant content type on page 1 (blog/product/tool/video)
- [ ] Intent as Google interprets it
- [ ] SERP features present (AI Overview, featured snippet, PAA, video)
- [ ] Average content length + entities/subtopics of top 5
- [ ] Average domain authority of ranking sites; any weak results beatable
- [ ] Content-format gap (e.g., no video where video serves intent)

## Prioritization — the authority-relative ladder

Score = volume × intent value × business relevance × feasibility at CURRENT authority. Work the
ladder bottom-up; each rung won makes the next winnable:

| Rung | Target | Why first |
|---|---|---|
| 1. Striking distance | Queries at positions 4-20 in GSC (yours) or competitor positions 4-20 (gap analysis) | Cheapest wins; the page already half-qualifies |
| 2. Function long-tail | KD 0-29 queries from the coverage method, especially tool/data/task queries where the site IS the answer | Winnable at any authority; compounds into cluster authority |
| 3. Cluster middles | KD 30-49 subtopic terms once the cluster's long-tail ranks | The cluster's internal links + demonstrated relevance carry them |
| 4. Head terms | KD 50+ | Only after rungs 1-3 and honest authority progress; until then the head-term play is often inclusion in the roundups/comparisons that DO rank |

Cadence: refresh striking-distance and rising-query lists monthly from GSC (rising queries are
Google telling you which functions it already associates with the site; feed them back into
step 3 of the coverage method).

## Low- and zero-volume reality

Keyword tools under-report niche, new-category, and long-tail demand, often to a flat "0".
For function queries, tool volume is a hint, not a gate:

- GSC impressions are ground truth: a "0-volume" query with impressions in GSC has demand.
- Autocomplete existence, PAA presence, and repeated community/site-search phrasing are demand
  evidence tools can't see.
- The sum of a function's long-tail variants routinely exceeds the head term's reported volume.
- Build for a demonstrated user task even at tool-zero when the site genuinely serves it; skip
  it when the only argument is "it might get impressions" (that is vanity visibility farming,
  anti-patterns.md).

## Measurement — non-branded is the SEO scoreboard

Track in GSC with the branded/non-branded filter (measurement-and-audit.md):

| Metric | Reading |
|---|---|
| Non-branded clicks trend | The SEO discovery engine: the number this file exists to move |
| Distinct non-branded queries with clicks | Coverage breadth; should grow as the map fills |
| Cluster-level average position | Rung progress on the ladder |
| Branded clicks trend | Brand marketing's scoreboard; report separately, never blended |

A rising branded line with a flat non-branded line is the exact pattern this file fixes: the
site is being found by people who already know it, and invisible to everyone else.
