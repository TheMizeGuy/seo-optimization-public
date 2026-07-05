# Changelog — seo-optimization (public)

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
