# Changelog — seo-optimization (public)

## 1.3.0 — 2026-09-22

Freshness release: the July → September 2026 delta (35 sourced findings, load-bearing items
re-verified on Google's own pages) plus a doctrine-consistency pass.

- Site reputation policy: the Aug 28, 2026 rewrite (four factors) and the EEA carve-out (no manual
  actions; the section is separated and ranks on its own); August 2026 spam update added; the 2026
  update record and "no core update since Jun 2" noted in penalty triage.
- Title rewrites: a third to three quarters of titles depending on the study's definition; over
  60 chars is almost always rewritten; Google's AI-headline test noted.
- Technical: crawl capacity is shared across all Google crawlers (Jul 22); canonical
  re-evaluation takes up to two weeks (Jul 10), added as a lag trap; internal-search blocking is a
  recommendation, not an Essentials guideline (Jul 31); crawlers send HEAD/OPTIONS/PUT/PATCH/DELETE;
  fetch caps 2MB (Search) / 64MB (PDF) / 15MB (general).
- Authority: HARO/Connectively closed Dec 2024 — replaced with Featured, Qwoted, Source of
  Sources, ProfNet; Reddit "no special preference" (Aug 2026) and its ChatGPT-citation collapse.
- Structured data: review-snippet fake / undisclosed-incentivized rule (Jul 24); return policy on
  Organization, not Offer (Sep 8); Course needs three courses plus Carousel; EEA aggregator and
  supplier units; LocalBusiness `@type` array and English opening-hours enumerations.
- Measurement: generative-AI performance report and control live worldwide since Aug 31;
  platform properties (YouTube/Instagram/TikTok/X); two GSC impression-history breaks (num=100
  removal Sep 2025; logging error May 2025–Apr 2026) with the compare-clicks rule; hreflang
  alternates are never indexed.
- AI search: dated September 2026 with an operational "Start here" block; AI Overviews
  auto-expanding into AI-Mode answers (Aug 28); Cloudflare's Sept 15 default flip and the
  Googlebot-blocking risk; the agent-friendly guide and UCP; citation-concentration volatility.
- Verticals: Google Business Profile Q&A removed (Ask button); Feb 2026 Discover core update;
  Preferred Sources button and Search profile badge; Merchant Center 2026 spec and sale-duration
  properties.
- Doctrine consistency: category-page copy must pass the naturalness gate; edge pre-render must be
  content-identical; image compression targets harmonized; "837 sites" correctly attributed to
  manual actions; unsourced mechanism claims hedged; the audit workflow no longer names a model.

## 1.2.0 — 2026-07-07

Accuracy release: audited fix wave over every reference file (29 findings; evidence-anchored).

- Index-bloat table corrected: robots.txt + canonical/noindex combos were self-defeating (a
  robots-blocked URL never shows Google its canonical or noindex); rows now give the correct
  mechanism and ordering (noindex while crawlable first; robots block only after drop-out).
- hreflang example corrected: "uk" IS the ISO 639-1 code for Ukrainian; the classic mistake is
  "en-uk" for the UK (should be "en-gb").
- Next.js App Router JSON-LD recipe corrected: plain `<script type="application/ld+json">` via
  `dangerouslySetInnerHTML` — not `generateMetadata()` (no JSON-LD field), not `next/script`.
- 503 guidance corrected to Google's actual tolerance (days, not "<2 weeks").
- GSC Mobile Usability report marked retired (Dec 2023) with the live replacement path.
- GSC branded/non-branded filter and chart-annotations rows labeled unverified, with an
  always-works brand-regex fallback for the non-branded scoreboard.
- Miscited statistics corrected or labeled: Google Images "22.6% of web traffic" (actually 2019
  share of searches), Reddit "97% of search queries", "hidden gems" update date (Nov 2023),
  programmatic-SEO 200-500% vendor claims, December 2025 core percentages, meta-description CTR
  figure, mobile search share, syndication "40% in a week".
- Harmonization: title-rewrite denominator unified, 70% long-tail stated once with label,
  internal vs external anchor-mix ranges explicitly scoped, entity-tactics deduplicated with the
  schema-is-not-a-GEO-lever caveat carried everywhere, CTR benchmarks attributed, recovery
  windows cross-referenced.

## 1.1.0 — 2026-07-05

Plugin packaging and documentation release. No skill-content changes from 1.0.0.

- Installable as a Claude Code plugin: `.claude-plugin/plugin.json` (repo root = plugin root,
  `skills/` auto-discovered) plus `.claude-plugin/marketplace.json`, so
  `claude plugin marketplace add TheMizeGuy/seo-optimization-public` followed by
  `claude plugin install seo-optimization@seo-optimization` just works. The clone-and-symlink
  install remains supported (use one method, not both).
- New `USAGE.md`: full use guide — trigger behavior, the engagement spine, three worked
  walkthroughs (deployed-site audit, non-branded demand capture, traffic-drop triage),
  everyday small asks, troubleshooting, update instructions.
- README rewritten around the plugin install path with a quickstart prompt list.
- GitHub Releases now accompany every version tag.

## 1.0.0 — 2026-07-05

Initial public release. Snapshot of the private skill after four hardening passes on this date:

- Deep-research refresh against primary sources (Google Search Central, Search Status Dashboard,
  official crawler docs) — 2026 core/spam update chronology, AI-search doctrine ("GEO is still
  SEO"), retired rich results, crawler map, superseded-claims ledger.
- Operational layer: live evidence toolchain, GSC lag discipline (LIVE-DEFECT / ALREADY-FIXED /
  INTENDED), seven-step traffic-drop triage runbook, sitemap sample-probing, CTR quick-win loop.
- Non-branded demand capture as a first-class lane: `reference/keyword-strategy.md`
  (function-query coverage, query→page map, authority-relative ladder, low-volume reality).
- Six-lane consistency/currency/actionability sweep: 21 fixes including unified striking-distance
  range, disavow/IndexNow execution details, back-button-hijacking spam policy, robots.txt
  ignored-directives list, 2MB fetch cap + WRS cache mechanics.

Behavioral verification: three pressure/application scenarios passed first-run on this snapshot
(GEO-hack refusal, GSC indexing-drop triage, brand-only-rankings demand capture).
