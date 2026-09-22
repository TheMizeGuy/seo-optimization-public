# Anti-patterns — the over-optimization catalog

What "bloat" and "junk optimization" mean concretely, how to detect them in your own output, and
what they cost. The naturalness gate and rationalization table live in SKILL.md; this file is the
full catalog behind them.

## Why this file exists

Google penalizes over-optimization harder than under-optimization, and the failure mode has
evolved. Crude spam (hidden text, stuffing) is algorithmically detected and largely extinct in
competent work. The live failure mode is **subtle, defensible-looking over-optimization**: each
element justified by a real signal, the sum reading as SEO'd. Engagement systems (NavBoost, per
the 2024 API leak and DOJ trial testimony) measure exactly that sum: a page that reads SEO'd gets
skipped, pogo-sticked, and demoted.

## Tier 1 — policy violations (manual-action territory)

Google spam policies, 2026. A manual action here requires cleanup + reconsideration (10–30 days);
structured-data actions strip ALL rich results site-wide.

| Violation | What it looks like | Severity |
|---|---|---|
| Scaled content abuse | Mass-produced pages (AI or human) primarily for ranking | Critical — March 2024's primary target |
| Site reputation abuse (parasite SEO) | Third-party or weakly owned content exploiting the host domain's authority. Policy rewritten Aug 28, 2026 ("Site reputation policy"): judged on presentation relative to the host, quality relative to the main domain, stated or implied authorship, and near-identical reuse across other sites | Critical outside the EEA — manual action on the affected section. Inside the EEA no manual actions (European Commission mandate): the section is separated in Google's systems and ranks on its own merits. Not a named target of the March/June/August 2026 spam updates |
| Expired domain abuse | Buying domains to exploit residual authority | Critical |
| Cloaking / sneaky redirects | Different content for bots vs users | Critical |
| Link schemes | Paid links without `rel="sponsored"`, PBNs, exchanges | High — a small site does not survive a link action |
| Doorway pages | Near-duplicate pages per query/geo variant | High |
| AI-response manipulation / impression farming | Pages created for fan-out/query variants, AI mentions, or vanity impressions rather than user tasks | High — scaled-content and AI-manipulation risk |
| Thin affiliation / scraped content | No original value added | High |
| Structured-data spam | Markup not matching visible content; fabricated ratings/reviews | Medium–High |
| Hidden text / links | CSS-hidden, zero-font, off-screen keywords | Medium |
| Back-button hijacking | Scripts trapping or rewriting browser history so Back keeps users on the site | High — named spam policy since April 13, 2026 |
| Keyword stuffing | Unnatural density in content or meta | Medium |

**AI content policy (2026 position):** creation method is not the violation — intent and quality
are. AI-assisted content with human editorial oversight and original value is fine; mass AI
content published to manipulate rankings is scaled content abuse. The test Google states: *was
this created primarily to help users, or primarily to rank?* Since May 15, 2026, Google's
documentation states the spam policies formally apply inside generative AI responses in Search
as well — the AI-response manipulation row above carries the same enforcement weight as classic
SERP spam.

**New adversarial risk (April 2026):** spam-report submissions can now directly trigger manual
actions, and the report text is forwarded verbatim to the penalized site owner. Competitors have
a formal channel — borderline tactics carry more downside than before.

## Tier 2 — the subtle class (the 2026 failure mode)

None of these violate a written policy. All of them degrade engagement signals, invite title
rewrites, and compound into algorithmic demotion. Every one was produced by a capable,
well-intentioned agent in baseline testing (2026-07-01) — these are the defaults to unlearn.

| Anti-pattern | What it looks like | Why it backfires |
|---|---|---|
| Title-tag keyword container | "Plant Care App with Watering Reminders & Houseplant Tracker \| Brand" | Reads as a list; the exact "excessive keywords" pattern that triggers Google's title rewrites (a third to three quarters of titles are rewritten depending on the study; over 60 chars almost always), so you lose control of your own snippet |
| Query-mapped architecture | One heading/section per target query instead of a user-need outline | Doorway thinking at section scale; produces repetitive structure users skim past |
| Entity stuffing | 4+ entities in one sentence justified as "entity coverage" | Keyword stuffing in 2026 clothes; entities earn relevance in explanatory context, not lists |
| Boilerplate keyword insertion | Keywords added to nav labels, footer straplines, copyright lines, taglines | The oldest stuffing pattern; boilerplate is discounted and the intent is legible |
| SERP-capture-first content | FAQ/sections written as "landing targets" rather than real questions | Content that answers nobody's actual question fails Needs Met and pogo-sticks |
| Word-count padding | "300 more words for depth" without new answers | Depth = new information; padding dilutes and NavBoost counts the bounce |
| Anchor-distribution gaming | Choosing anchors to hit an exact-match percentage | Distribution targets are smell detectors, not quotas; engineered distributions look engineered |
| Schema maximalism | Types added for eligibility, not because the page IS the thing | FAQ rich results are dead (May 2026); Google's AI features don't require structured data (official, May 2026); mismatch is Tier 1 |
| Freshness faking | Bumping dates without content changes | Google triangulates bylineDate / syntacticDate / semanticDate (API leak); disagreement is detectable |
| Meta-keyword-era relics | `<meta name="keywords">`, keyword-list alt text on decorative images | Ignored at best; stuffing signal at worst |
| Internal-link saturation | Every mention of every term linked | Dilutes equity, unreadable; 2–5 contextual links per 1,000 words is the norm |
| Cannibalization by expansion | New page per query variant | Pages compete at positions 5–15 instead of one page winning; consolidate + 301 |
| Vanity visibility farming | Publishing pages because they might earn impressions, AI mentions, or long-tail fan-out coverage, with no expected click, engagement, brand, or conversion value | Trains the site toward low-satisfaction sessions; looks like scaled content when repeated |
| llms.txt cargo cult | Shipping llms.txt "for AI visibility" | Settled no: Google documented ignoring it (June 2026); 300K-domain study found zero citation effect. Only real use: docs sites consumed by coding agents |
| Tool-metric cargo cult | Optimizing for invented metrics | "Engagement Reliability" (2026) is a fabricated CWV metric circulating in SEO content mills. Verify every metric against Google primary sources |

## Detection heuristics — audit your own output

Run these against any page you just optimized:

1. **Read the title aloud.** If it sounds like a list or contains two query phrases spliced with
   "with"/"&"/",", rewrite to one phrase + differentiator.
2. **Trace every heading.** For each, name the user question it answers. Any heading whose origin
   is the keyword list, not the outline, gets rewritten or merged.
3. **Count entities per sentence.** A sentence naming 4+ products/species/brands is an inventory,
   not an explanation, unless the list itself is the content (a "supported X" section is fine).
4. **Diff the boilerplate.** If your optimization pass touched nav labels, footer text, taglines,
   or copyright lines, revert unless the natural label happens to be the keyword.
5. **Justification audit.** For every change, state the reader benefit in one sentence without
   using the words "signal", "relevance", "keyword", or "ranking". Can't? Revert it.
6. **Schema parity check.** Every JSON-LD claim must be visible on the rendered page; every
   rating/review must exist in a verifiable source.
7. **Impression-quality audit.** If impressions are rising while clicks, engaged sessions,
   branded demand, conversions, citation quality, and repeat visits stay flat/down, you're farming
   visibility rather than building demand. Stop expanding pages until the existing pages satisfy.
8. **Live-verify before fixing.** A GSC-sourced finding whose last crawl predates your latest
   deploy may already be fixed. Classify LIVE-DEFECT / ALREADY-FIXED / INTENDED
   (measurement-and-audit.md) before shipping changes; redundant "fixes" are churn with real
   regression risk (production case: stripping a query param for marginal crawl-budget gain
   would have broken user-facing version context).
9. **The deletion test.** If Google vanished tomorrow, which of your changes would you keep?
   The ones you'd delete were bloat.

## Penalty triage and recovery

| Signal | Diagnosis | Path |
|---|---|---|
| GSC manual-action notification | Manual action | Fix every listed violation → document → reconsideration request (10–30 days). Honest, specific, evidence-backed |
| Drop coincides exactly with a confirmed update (check the Search Status Dashboard; 2026 so far: Feb Discover core, Mar spam, Mar core, May core, Jun spam, Aug 18-20 spam — no core update since Jun 2 as of Sep 22, 2026, while tracker volatility ran hot) | Algorithmic | No reconsideration exists. Fix quality; recovery lands at subsequent core updates — 6–24 months, and core updates can be a quarter or more apart. A tracker spike without a dashboard entry is not an update |
| Gradual decline over months | Decay/competition | Content refresh + gap analysis, not penalty response |
| One template affected | Template-level thinness | Fix or noindex the template |

Recovery sequence for algorithmic hits: triage (confirm timing vs rollout) → remove/noindex thin
and parasitic content → rebuild E-E-A-T and depth → sustain; the Helpful Content classifier
operates site-level, so one bad section drags everything, and it re-evaluates over months, not
days. Never panic-edit mid-rollout.

## The disposition

The user-facing statement of this whole file: **optimize nothing you can't defend to a reader.**
Every technique that works long-term makes the page better for the person on it; every technique
that only works short-term is a future traffic drop with a date you don't get to pick.
