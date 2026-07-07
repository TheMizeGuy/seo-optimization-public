# Changelog — seo-optimization (public)

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
