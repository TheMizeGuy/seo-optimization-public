# Technical SEO Reference

Actionable technical-SEO core for auditing and fixing any site: crawling/indexing, rendering, status codes, Core Web Vitals, and server config. Naturalness gate and workflow live in the parent SKILL.md; query research lives in keyword-strategy.md.

## Crawling and Crawl Budget

Crawl budget = crawl rate limit (max requests/sec your server tolerates) x crawl demand (how much Google wants the content).

| When crawl budget matters | When it doesn't |
|---|---|
| Sites at Google's official thresholds — 1M+ unique pages updating weekly OR 10K+ pages changing daily — or many important URLs stuck "Discovered — currently not indexed" | Small and medium sites — crawl budget is rarely the constraint; quality, linking, canonicals, and server errors usually matter more |

Crawl capacity factors: site speed (faster = higher limits), 5xx errors (reduce crawling), hostload backoff. Crawl demand factors: popularity, staleness (frequently-changing pages recrawled faster), site events (migrations spike demand), duplicate content (wastes budget).

### Crawl budget optimization checklist

- [ ] Eliminate soft 404s — return explicit 404/410 for dead pages (200-with-"not-found"-content wastes recrawls)
- [ ] Fix redirect chains — max 1 hop; kill chains of 3+
- [ ] Block low-value URLs in robots.txt: faceted navigation, internal search results, print pages
- [ ] Canonicalize duplicates, don't just block — blocked pages waste budget and leak equity
- [ ] TTFB target <200ms; enable Gzip/Brotli
- [ ] `robots.txt` blocked pages stay in Google's queue — use 404/410 for pages that should disappear (Google official)
- [ ] noindex still costs a fetch (Google crawls, sees the tag, then drops); robots.txt is more budget-efficient when you don't need the page rendered

Key distinction: **robots.txt blocks crawling, noindex blocks indexing.** Using robots.txt to "prevent indexing" is a classic trap — a blocked URL can still be indexed from external links, and Google never sees the noindex on a page it can't crawl.

### Log file analysis (large sites)

| Metric | Reveals |
|---|---|
| Crawl frequency per URL | Which pages Google prioritizes |
| Response codes served to bots | 5xx errors wasting budget |
| Crawl of orphan pages | Pages discovered via stale sitemaps/backlinks with no internal links |
| Bot distribution | 2026: Googlebot, Bingbot, GPTBot, ClaudeBot, PerplexityBot all compete for server resources |
| Time-to-crawl for new content | Discovery latency |

## robots.txt

Domain root only (`/robots.txt`). Pattern:

```
User-agent: *
Disallow: /search/
Disallow: /cart/
Disallow: /checkout/
Disallow: /account/
Disallow: /admin/
Disallow: /*?sort=
Disallow: /*?filter=
Allow: /

Sitemap: https://example.com/sitemap.xml
```

Google's parser honors only `user-agent` / `allow` / `disallow` / `sitemap`. It silently ignores
`crawl-delay`, `noindex`, `nofollow`, `noarchive`, `host`, `clean-param`, and — documented April
2026 — `content-signal`, `content-usage`, `domain`, `request-rate`, `revisit-after`,
`visit-time`. `content-signal` is Cloudflare's Content Signals Policy field: adding it has zero
effect on Google regardless of what it signals to other crawlers.

### Classic robots.txt traps

| Trap | Impact |
|---|---|
| Blocking CSS/JS resources | Googlebot can't render the page; content invisible |
| Blocking `/api/` when client-rendered content depends on it | Content never indexed |
| Using robots.txt to prevent indexing | Prevents crawling, not indexing — use `noindex` |
| `Disallow: /` wildcard overkill | Blocks the entire site |
| 404 on robots.txt | Google assumes everything crawlable (wasteful, not fatal) |

2026 AI bot management: differentiate search-retrieval bots from training scrapers using the three-tier crawler map in `ai-search-geo.md` §7 (current tokens per operator, the Google-Extended trap, Cloudflare's default-block escalation). Blocking a search/retrieval bot removes you from that engine's answer surfaces.

## XML Sitemaps

**Golden rule: every sitemap URL must simultaneously return HTTP 200, be the canonical version, and carry no noindex.**

| Practice | Detail |
|---|---|
| Max size | 50,000 URLs or 50MB per file; sitemap index beyond that |
| Segmentation | One sitemap per content type (products, blog, categories) — isolates diagnostics |
| `<lastmod>` | Only when content actually changed; never auto-update timestamps |
| Generation | Dynamic preferred — auto-excludes 404s, redirects, noindexed pages |
| Image/video sitemaps | For media-heavy sites and visual-intent niches (image-search reach data: on-page-and-content.md § Image Optimization) |
| Submission | GSC > Sitemaps |

Sitemap inclusion is a **weak canonical signal** — Google defaults to sitemap URLs as canonical only when no strong signals (301, `rel="canonical"`) exist.

**Verify by sampling, not by trust:** fetch 10-30 random `<loc>` URLs from each sitemap and
confirm every one returns 200, is self-canonical, and carries no noindex. Generators leak 404s
and redirects under specific parameter scopes (one production sitemap shipped ~10% 404s from a
single unguarded query-param path); a homepage spot-check never catches this. A large
sitemap-count vs GSC-Indexed gap is a quality/architecture verdict, not a submission problem:
diagnosis in measurement-and-audit.md.

## Canonical Tags

`<link rel="canonical" href="https://www.example.com/preferred-page/" />`

Use for: www/non-www, HTTP->HTTPS, trailing-slash variants, URL parameters, syndicated content (point to original), AMP->canonical HTML. **Self-referential canonicals are best practice even without duplicates.**

| Canonical error | Impact |
|---|---|
| Canonical points to 404/redirect | Google ignores it |
| Paginated pages canonicalized to page 1 | Google may ignore; deep content lost |
| Conflicting signals (canonical says A, redirect goes B) | Google picks unpredictably |
| Cross-domain canonical without proper setup | May be ignored |
| Dynamic canonical from URL parameter | Circular references |

**35% of audited sites** have errors in at least one of robots.txt/sitemaps/canonicals (Screaming Frog 2025); the most common failure is lack of coordination between the three systems — check them as one unit.

## Indexing Signals and Troubleshooting

Signal strength (priority order): `rel="canonical"` and 301 (strong directives) > sitemap inclusion and internal links (weak hints). `noindex` meta / `X-Robots-Tag` header = absolute.

### Index bloat prevention

| Bloat source | Fix |
|---|---|
| Faceted navigation URLs | Low-value facet combinations: robots.txt block (accept that stray URLs may still index title-only from external links); facets you keep crawlable: canonical to base category. Never both on one URL — a canonical on a robots-blocked page is never seen (see Key distinction above) |
| Paginated archives | canonical to page 1 or view-all |
| URL parameters (sort/filter/session) | canonical |
| Thin tag/author archives | noindex or consolidate |
| Internal search results | noindex (crawlable) is the de-indexing mechanism; robots.txt block is the crawl-budget mechanism for paths never indexed. To remove already-indexed search URLs: noindex first, add the robots block only after they drop out — a robots-blocked noindex is never seen |
| Staging/dev environments | Password-protect or noindex + robots.txt — **classic trap: noindex left on after staging goes live; check first on any "site vanished" report** |

### GSC Page Indexing statuses

| Status | Action |
|---|---|
| Discovered — currently not indexed | Improve internal linking, submit in sitemap, request indexing |
| Crawled — currently not indexed | Improve content quality/uniqueness (see below) |
| Duplicate without user-selected canonical | Set explicit canonicals |
| Duplicate, Google chose different canonical | Investigate why Google prefers the other URL |
| Excluded by noindex tag | Remove noindex if page should rank |
| Blocked by robots.txt | Update robots.txt if page should be crawled |
| Not found (404) | Fix URL or redirect |

"Crawled — not indexed" fixes: add substantial unique content (500+ words of genuine value); differentiate or consolidate near-duplicates; build authority; add E-E-A-T signals (author, credentials, citations); reduce programmatic scale / increase per-page uniqueness; audit site-wide quality. Context: Google's May 2025 quality review actively removed pages; the indexing quality threshold has permanently risen — mass-produced unedited AI content loses crawl priority.

## HTTP Status Codes for SEO

| Code | Link equity | Index behavior | Use |
|---|---|---|---|
| 301 | Passes | New URL indexed, old drops | Permanent moves, migrations |
| 302 | Not transferred | Old URL stays indexed | Temporary (A/B tests, maintenance) |
| 307/308 | As 302/301 | Same | Method-preserving variants |
| 304 | — | Saves crawl budget | If-Modified-Since caching |
| 404 | — | Removed eventually (months) | Page missing, reason unknown — Google rechecks periodically |
| 410 | — | **Faster removal** | Content deliberately, permanently removed |
| 451 | — | Removed | Legal takedowns |
| 500 | — | Reduced crawl rate if persistent | Never intentional |
| 503 | — | Bots pause; safe for short outages (a day or two). Crawl rate drops while it persists; beyond ~a week expect pages to start dropping | Planned maintenance — keep windows minimal + `Retry-After` header |

Soft 404 anti-pattern: 200 OK with "not found" content — always return explicit 404/410. Prefer 410 over 404 for known-removed content.

## HTTPS and URL Structure

HTTPS is a confirmed ranking signal since 2014. Checklist: valid auto-renewing cert; site-wide 301 HTTP->HTTPS; zero mixed content; HSTS (`Strict-Transport-Security: max-age=31536000; includeSubDomains`); canonicals/sitemap/internal links all HTTPS.

| URL practice | Rule |
|---|---|
| Short, descriptive | `/seo/technical-guide/` not `/p?id=12345` |
| Hyphens, lowercase | Not underscores; not mixed case |
| No special chars in paths | Avoid `%20`, `&`, `=`, `#` |
| Logical hierarchy | Mirrors site structure; key pages within 3 clicks of homepage |
| Trailing slash | Pick one, canonicalize, enforce with a single 301 rewrite |
| URL changes | 301 map old->new 1:1; no chains; monitor GSC after migration |

## JavaScript SEO and Rendering

Googlebot fetches HTML, queues renderable 200 responses for Web Rendering Service, then indexes
the rendered HTML when resources are available. Rendering can be quick but is not something to
depend on for public content; client-side-rendered apps that deliver empty initial HTML still risk
delayed/incomplete indexing and weaker non-Google AI visibility.

Two documented fetch/render mechanics that bite audits (Google crawler docs, 2026):

- Googlebot fetches/renders only the **first 2MB uncompressed** of an HTML resource (the cap
  applies per-resource to JS/CSS too); past-cutoff bytes are silently dropped and the truncated
  document is indexed as if complete. Keep meta, canonical, and JSON-LD before any large inlined
  state/JSON blob, never after.
- WRS keeps its own **~30-day JS/CSS cache independent of HTTP caching headers** (and is
  stateless between requests). A shipped JS/CSS fix may not show in rendered captures for weeks;
  treat that as cache lag, not a broken deploy.

| Strategy | SEO friendliness | Use case |
|---|---|---|
| SSR / SSG / ISR / hybrid | Excellent | Public content of any kind |
| CSR | Poor | Authenticated dashboards only |

Critical rules:

1. Critical content in initial HTML (SSR/SSG)
2. Crawlable `<a href>` links — never JS-only navigation
3. Proper HTTP status codes server-side
4. Never block JS/CSS in robots.txt (rendering needs them)
5. No `#` fragment URLs for content routing
6. `<title>`/`<meta>` server-side, not client-side
7. Verify with GSC URL Inspection "Live Test" (shows rendered HTML)

## Core Web Vitals

Ranking weight: modest — a tie-breaker that matters most where content quality is already matched;
it never substitutes for the content work at the top of SKILL.md's weight table. Late-2025 CrUX
pass rate was ~54% overall (research refresh, superseding the old 47% figure). Google ranks on
**field data (CrUX, 75th percentile)**, not lab — a Lighthouse 100 can still fail CWV in the field.
Lab (Lighthouse/WebPageTest) is for debugging only; Lighthouse cannot directly measure INP without
real user interaction, so use TBT as a lab proxy.

| Metric | Good | Needs improvement | Poor | Measures |
|---|---|---|---|---|
| LCP | <= 2.5s | 2.5–4.0s | > 4.0s | Largest visible element render |
| INP | <= 200ms | 200–500ms | > 500ms | Input responsiveness (replaced FID March 2024) |
| CLS | <= 0.1 | 0.1–0.25 | > 0.25 | Layout stability |

Pass rates (late-2025 CrUX/Web Almanac direction): LCP remains the hardest to pass and most
impactful to fix; INP/CLS usually pass more often. Treat any 2026 claim of new CWV thresholds or
metrics ("Engagement Reliability") as false unless verified in Google/web.dev docs — full entry:
anti-patterns.md, tool-metric cargo cult.

## Rendered Production Capture

For deployed technical audits, source HTML is not enough. Capture what Google can fetch and what
the rendered DOM exposes:

```bash
curl -sI -A 'Googlebot/2.1 (+http://www.google.com/bot.html)' https://example.com/page
curl -sL -A 'Googlebot/2.1 (+http://www.google.com/bot.html)' https://example.com/page \
  | rg -i '<title|canonical|robots|hreflang|application/ld\+json'
curl -s https://example.com/robots.txt
curl -s https://example.com/sitemap.xml | xmllint --noout -
npx lighthouse https://example.com/page --form-factor=mobile --only-categories=performance
```

Then verify the same URL in Search Console URL Inspection: indexed canonical, crawl allowed,
rendered HTML, screenshot, discovered structured data, and any page-indexing/CWV/enhancement
issues. Production capture wins over repo assumptions when they disagree.

Behind a CDN or bot-protection layer, a blocked/challenged curl is not evidence about Googlebot:
probe the origin directly (container/SSH curl against localhost) AND through the edge. The edge
answer is what Google sees; the origin answer isolates whether the app or the edge config is at
fault. And before fixing anything GSC reported, apply the lag discipline in
measurement-and-audit.md; the report may describe a state you already shipped past.

### LCP (highest-leverage fixes first)

| Fix | Impact |
|---|---|
| Preload LCP image: `<link rel="preload" as="image" href="hero.webp" fetchpriority="high">` | Critical |
| `fetchpriority="high"` on the LCP element | Critical |
| **Never lazy-load the LCP image** — remove `loading="lazy"` from it (classic trap: blanket lazy-loading including the hero) | Critical |
| TTFB <200ms (caching, CDN, hosting) | High |
| WebP/AVIF (25-50% smaller than JPEG) | High |
| Inline critical CSS; `async`/`defer` non-critical scripts | High |
| Right-sized images; Brotli/Gzip; minimize redirects; preconnect critical origins | Medium |

LCP budget: TTFB <800ms + resource load <800ms + render delay <500ms = <2,100ms (400ms margin under the 2.5s target).

### INP

| Fix | Impact |
|---|---|
| Break long tasks (>50ms) with `scheduler.yield()` / `setTimeout` | Critical |
| Remove unused JS (DevTools Coverage); defer/async non-critical scripts | High |
| Web workers for computation; lazy-load chat widgets, defer analytics | High |
| DOM size <1,500 elements; debounce input handlers; avoid forced synchronous layout | Medium |
| Framework hydration cost | Progressive/partial hydration, islands |

### CLS

| Source | Fix |
|---|---|
| Images/iframes without dimensions | Explicit `width`/`height` or `aspect-ratio` |
| Ads loading dynamically (worst offender on ad-heavy sites) | Reserve space: `.ad-container { min-height: 250px }` |
| Web fonts (FOIT/FOUT) | `font-display: swap` + preload critical fonts |
| Dynamic content injection | Reserve space; never insert above existing content |

Debug: DevTools Performance > Layout Shifts; Web Vitals extension; Layout Instability API.

### Performance budget (reference targets)

Total page <1.5MB mobile · JS <300KB compressed · CSS <100KB · above-fold images <500KB · fonts <100KB (2 weights max of 1 family) · third-party <200KB · <50 initial requests · TTFB <200ms.

## Resource Hints

| Hint | Does | Cost | Rule of thumb |
|---|---|---|---|
| `dns-prefetch` | DNS only | Minimal | Use broadly; fallback for non-preconnect browsers |
| `preconnect` | DNS+TCP+TLS | Low | **Max 2-3 origins** (~300ms connection overhead each) |
| `preload` | Full download | Medium | Only first-render-critical (LCP image, critical CSS/font); overuse starves bandwidth |
| `prefetch` | Low-priority next-nav download | Low | High-probability next page only |
| `prerender` | Full background render | High | Near-certain next page only |

Font preload needs `crossorigin`: `<link rel="preload" as="font" type="font/woff2" crossorigin>`. HTTP `Link` header works for preconnect/preload.

## Font Optimization

- WOFF2 only (30% better compression than WOFF, universal support); drop WOFF/TTF/EOT
- `font-display: swap` for body text; `optional` for decorative; `block` only for icon fonts
- Preload 1-2 critical fonts; subset with `unicode-range` (Latin for English-only)
- 3+ weights of one family -> variable font (40-60% size reduction, `font-weight: 100 900`)
- Max 2 families, 2-3 weights total; self-host (kills third-party connection overhead); total <100KB

## Edge SEO

Modify responses at CDN/edge (Cloudflare Workers, Vercel Edge, Lambda@Edge) without touching origin: dynamic 301 management, JSON-LD/hreflang injection, title A/B tests, bot-specific pre-rendered HTML, `X-Robots-Tag`/canonical via headers, edge-side rendering (TTFB reduction 60-80%, internal-benchmark figure), bot-request logging.

## IndexNow and Instant Indexing

Before the first POST: host the key as a plain UTF-8 `{key}.txt` file at the domain root (`https://{host}/{key}.txt`); submissions fail verification without it. Then `POST https://api.indexnow.org/indexnow` with `{host, key, urlList}` on publish/update. Supported: Bing, Yandex, Seznam, Naver. **Google does NOT support IndexNow** — use GSC URL Inspection or the Indexing API (officially JobPosting/BroadcastEvent only; 200-request default quota).

## Server Configuration Essentials

| Concern | Setting |
|---|---|
| Compression | Brotli preferred (`brotli_comp_level 6`) + Gzip fallback (`gzip_comp_level 5` — the sweet spot: 1-4 too little, 6-9 marginal gain for heavy CPU); cover text/css/js/json/xml/svg |
| Static asset caching | `expires 1y; Cache-Control: public, immutable` on images/css/js/woff2/svg |
| HTML caching | Short TTL: `expires 1h; Cache-Control: public, must-revalidate` |
| Redirect consolidation | One 301 each for HTTP->HTTPS, www choice, trailing slash — never chained |
| HSTS | `Strict-Transport-Security: max-age=31536000; includeSubDomains; preload` (SEO-relevant: forces HTTPS) |
| Security headers | `X-Content-Type-Options: nosniff`, `X-Frame-Options: SAMEORIGIN`, `Referrer-Policy: strict-origin-when-cross-origin`, `Permissions-Policy` minimal, CSP per site |
| Page-level directives via header | `X-Robots-Tag: noindex` / `noarchive` for non-HTML resources |

## Keyword Research

Moved to `keyword-strategy.md` — full research pipeline, KD validation, SERP-overlap clustering,
the function-query coverage method, the query→page map, and the authority-relative
prioritization ladder live there.

## Classic Traps (quick audit list)

1. LCP image lazy-loaded (`loading="lazy"` on the hero)
2. robots.txt blocking CSS/JS/API routes that rendering depends on
3. noindex or robots.txt block left on after staging -> production
4. robots.txt used to "de-index" (blocks crawling, not indexing)
5. Soft 404s (200 + "not found" content)
6. Redirect chains (HTTP -> www -> slash as 3 hops instead of 1)
7. Sitemap listing non-canonical / noindexed / redirecting URLs
8. Canonical pointing at a 404 or redirect; canonical vs 301 disagreement
9. `<lastmod>` auto-updated on every deploy (destroys the freshness signal)
10. Titles/meta injected client-side only; content invisible in Wave 1 HTML
11. Trusting one tool's KD or a Lighthouse lab score instead of SERP reality / CrUX field data
12. Uncoordinated robots.txt + sitemap + canonicals (the single most common audit failure — Screaming Frog 2025)
