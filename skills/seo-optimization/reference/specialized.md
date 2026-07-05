# Specialized SEO Reference

Purpose: "does my situation have special rules?" lookup — condensed essentials per specialty (local, mobile/international, video/image, news/publisher, e-commerce, platform, migration, accessibility/UX, YMYL, explicit content). Sections carry a source pointer where a deeper reference exists; remaining sources are consolidated per the Google documentation links inline.

---

## Local SEO

Highest-ROI SEO investment for businesses with physical locations. Google Business Profile (GBP) is the single most important asset.

### GBP essentials

| Element | Rule |
|---|---|
| Business name | Exact legal name — keyword stuffing is a policy violation |
| Categories | Most specific primary + up to 9 secondary |
| Address / phone | Must match website and all citations exactly; local number > toll-free |
| Description | 750 chars: services, areas served, differentiators |
| Photos | 10+, add weekly — businesses with photos get 42% more direction requests |
| Posts / Q&A | Keep updates current and answer real questions where the surface supports it; never seed fake questions or reviews |

### Local pack ranking

- Official Google frame: **Relevance, Distance, Prominence**. There is no way to request or pay
  for better local ranking.
- Signal categories: GBP completeness, reviews (quantity/score/recency/keywords), NAP consistency, local backlinks, citations, behavioral (CTR, direction requests, calls).

### NAP consistency

NAP = Name, Address, Phone — must be **exactly identical** everywhere (watch "Suite 200" vs "Ste 200", "LLC" vs no-LLC, phone formats, stale old addresses).
Tier 1 citations: Google Business Profile, Apple Maps, Bing Places, Yelp, Facebook. Push corrections via data aggregators (Data Axle, Foursquare, Localeze); re-audit quarterly.

### Reviews

| Stat (internal benchmark) | Value |
|---|---|
| Consumers influenced by reviews | 71% |
| Trust businesses with more reviews | 74% |
| Credibility minimum | 10+ reviews (ideal: 50+) |
| Recency | Reviews from last 90 days weighted most |
| Responding to reviews | Perceived 1.7x more trustworthy; Google tracks response rate/speed |

Respond to negatives within 24 hours; resolve offline; never argue.

### On-page

- Multi-location: one unique page per location — unique H1 ("[Service] in [City]"), 500+ unique words, local landmarks, embedded map, location-specific LocalBusiness schema + photos.
- Schema: use the most specific `@type` (`Restaurant`, `Dentist`, `LegalService`) not generic `LocalBusiness`; include address, geo, telephone, openingHoursSpecification, aggregateRating (real collected reviews only — fabricated ratings are a site-wide manual action, SKILL.md common mistakes).

---

## Mobile and International SEO

### Mobile-first (applies to 100% of websites)

Google indexes the **mobile version**. Mobile search share: 58% of Google searches (2025). 53% of mobile users leave if load >3s.

Parity checklist (mobile must equal desktop):
- [ ] Identical text content (nothing hidden on mobile)
- [ ] Same images + alt text, same videos + metadata
- [ ] Same JSON-LD, meta tags, robots directives, internal links
- [ ] Lazy-loaded core content accessible without user interaction (no "tap to expand")

Mobile UX floors: 48x48px touch targets (8px spacing), 16px body font, viewport meta tag, no horizontal scroll, no full-screen entry popups (penalty — see Interstitials section), clickable `tel:` links.

### AMP (legacy/mobile publishing)

AMP is indexed like any other web page and must meet the same quality, indexing, and structured
data standards. It is not a ranking shortcut, and AMP content continues to rank like ordinary
pages.

Current Google Search posture as of 2026-07-01:
- Google Search takes users directly to publisher AMP host pages; do not build or maintain AMP
  around old AMP Viewer, AMP Cache, or signed-exchange assumptions.
- AMP pages must let users experience the same content and complete the same actions as the
  canonical page where possible.
- Use a sensible same-site AMP URL scheme, valid AMP HTML, and structured data that follows the
  normal Google structured-data policies.
- For new builds, default to fast responsive canonical HTML unless AMP has a clear production or
  distribution reason.

### International — URL structure

Recommended default: **subdirectories** (`example.com/de/`) — consolidates link equity, adequate geo-targeting with hreflang. ccTLD = strongest geo-signal but splits equity and costs the most to maintain; URL parameters = worst option.

### Hreflang — the three non-negotiables

1. **Self-referencing** — every page includes an hreflang pointing to itself.
2. **Symmetric** — if A points to B, B must point back to A.
3. **Valid ISO codes** — language ISO 639-1 (en, de), region ISO 3166-1 Alpha-2 (US, GB). Always include `x-default` as fallback.

Methods: HTML `<link>` tags (<100 combos), XML sitemap annotations (large sites), HTTP headers (PDFs).

### Classic hreflang mistakes (75% of international sites have hreflang errors that fragment rankings — industry audit data)

| Error | Consequence |
|---|---|
| Missing self-reference | Google may ignore ALL hreflang on that page |
| Non-symmetric annotations | Broken language targeting |
| Wrong codes (classic example: "uk" used for Ukrainian — should be "ua") | Wrong-audience targeting |
| Pointing at non-200 pages | Annotation ignored |
| Missing x-default | No fallback for unmatched users |
| Hreflang on non-canonical URLs | Conflicts with canonical signals |

Localization: transcreate, don't translate — local keyword research per market, local examples/CTAs/currency. Create separate GSC properties per country/language version.

---

## Video and Image SEO

### Video

- 25%+ of Google search results include video; YouTube is the 2nd largest search engine globally.
- **VideoObject schema is required for video rich-result eligibility**: name, description, thumbnailUrl, uploadDate, duration (ISO 8601 e.g. `PT8M30S`), contentUrl/embedUrl. Add `hasPart` Clip entries (name + startOffset/endOffset) → "key moments" carousel in Google SERPs.
- **Chapters**: every 90-120 seconds, minimum 3 (YouTube requirement for chapter UI), descriptive names, `0:00 Intro` format in description. Chapter markers: +11% average watch time (internal benchmark).
- **Transcripts**: upload custom transcripts (auto-captions inaccurate) AND publish on-page below the embed with headings/links — the most important indexable text for video.
- Optimal length 5-10 min (31.5% average retention, internal benchmark).

### Image

Google Images delivers **22.6% of all web traffic** (internal benchmark) — not optional.

| Format | vs JPEG | Support (2025) | Use |
|---|---|---|---|
| AVIF | 50% smaller | 90%+ | Photos (primary) |
| WebP | 25-35% smaller | 98%+ | Photos (fallback), animations |
| SVG | vector | universal | Icons, logos, diagrams |
| PNG | lossless | universal | Transparency graphics |

- Serve via `<picture>` progressive enhancement (AVIF → WebP → JPEG fallback) with explicit `width`/`height` and `srcset`/`sizes`.
- **The #1 image performance regression in 2026 audits: lazy loading the LCP image.** LCP image gets `fetchpriority="high"` and NO `loading="lazy"`; below-fold images get `loading="lazy"`.
- Alt text: ~125 chars, descriptive and specific, no "Image of...", empty `alt=""` only for decorative images.
- Preferred image signals: set the page's best representative image consistently in structured
  data `image` and `og:image`; for Discover/news, use at least 1200px-wide images and
  `max-image-preview:large`.
- Image sitemap (`<image:image>` with loc/title/caption) for image-heavy sites.
- Compression targets (internal benchmarks): thumbnails <30KB, content images <100KB, hero <200KB, above-fold total <500KB combined.

---

## News and Publisher SEO

Use this section for publishers, current-events blogs, editorial newsletters with public article
archives, and any site requesting Google News, Top Stories, or Discover visibility.

### Eligibility floor

- Clear publisher identity: About page, editorial policy, corrections policy, contact info,
  bylines, author pages, and visible dates.
- Original reporting or analysis. Summarization-only news content is fragile in Search, Discover,
  and AI summaries.
- Article schema with author, datePublished, dateModified, image, publisher, and canonical URL.
- Avoid misleading date bumps. Update timestamps only when the article materially changes.
- Separate opinion, sponsored, syndicated, and wire content clearly.

### News sitemap

Google News sitemaps are only for news publishers and only for fresh news URLs:

| Rule | Requirement |
|---|---|
| Freshness window | Include articles from the last 2 days only; remove older URLs or remove the `news:` metadata |
| Sitemap size | Max 1,000 `<news:news>` entries per sitemap |
| Required fields | publication name, language, original publication date/time, title |
| Tracking | Separate news sitemap can make Search Console monitoring cleaner |

Do not create a new sitemap file for every update; update the existing sitemap as articles publish.

### Discover / Top Stories posture

- Large crawlable images: 1200px+ and `max-image-preview:large`.
- Non-clickbait titles that still make the story specific and worth opening.
- Fast mobile UX and clean ad/interstitial behavior.
- Original photos, documents, datasets, interviews, or local reporting whenever possible.
- Preferred Sources is a publisher/audience feature: if the site is eligible, readers can select
  the domain or subdomain as a preferred source. It can surface badges in Top Stories and, since
  May 2026, AI Overviews and AI Mode. Treat this as audience development, not a ranking hack.

### Paywalls, subscriptions, and Web Stories

Paywalled publishers must use Flexible Sampling, not cloaking. Metering and lead-in models are
acceptable patterns; Google recommends cautious experiments because excessive paywall exposure can
degrade user satisfaction and rankings. Enclose paywalled portions with paywall structured data so
Google can distinguish a legitimate paywall from showing Googlebot different content than users.

Web Stories are a separate Search/Discover visual format, not a substitute for article SEO. Use
them only when the story benefits from a mobile-first visual narrative, original perspective, and
clear narrative arc; keep the canonical article or landing page strong.

---

## E-Commerce SEO

### Product pages

- Unique description 150-300 words minimum — **never manufacturer copy**.
- Product schema: name, image[], description, sku, brand, offers (price, priceCurrency, priceValidUntil, availability, itemCondition), aggregateRating (real ratings only).
- Variant schema (2025+): nest variants under `hasVariant` with per-variant color/size/offers.
- Merchant listing consistency: structured data, Merchant Center feed, visible product page,
  shipping, returns, loyalty, price, and availability must agree. Google can use Merchant Center
  for free listings and AI/Search product surfaces; stale markup creates diagnostics noise and
  poor user trust.
- Adult-oriented products: use `hasAdultConsideration` in Product / Merchant listing / variant
  markup where applicable, and keep Merchant Center feed adult-product signals consistent. Do not
  apply adult metadata sitewide unless the site or section is explicitly adult.
- Breadcrumbs with BreadcrumbList schema; visible FAQ section answering real buyer questions (FAQ rich results retired May 2026 — the markup itself earns nothing); related-product internal links.

### Category pages

Rank for broad commercial keywords product pages can't. Add 200-400 words of SEO content **below the product grid** (above pushes products under the fold). CollectionPage/OfferCatalog schema. Never create indexable URL variants for sort parameters.

### Faceted navigation (the biggest e-comm technical challenge)

Progressive rule (internal benchmark):

```
1 filter applied:  index IF search demand exists; noindex otherwise
2 filters applied: always noindex
3+ filters:        always noindex; consider robots.txt block
Sort parameters:   always block via canonical or robots.txt
```

Implementation options: dynamic noindex by filter count, canonical to base category (default for filtered pages), `Disallow: /*?color=` robots patterns, JS-only filtering when no filter URLs should exist.

### Pagination

`rel="prev"/"next"` deprecated by Google in 2019. Recommended for large catalogs: **hybrid** — "Load More" button for UX, but paginated URLs (`?page=2`) exist in source HTML, each with self-referential canonical, included in the sitemap. Canonicalizing all pages to page 1 hides deep products from Google.

### Out-of-stock

| Scenario | Action |
|---|---|
| Temporarily out | Keep live, "Out of Stock" badge, update schema `availability` |
| Permanently discontinued | 301 → closest alternative or parent category |
| No redirect target | 410 Gone |

**Never 404 a product page that has backlinks** — redirect to preserve equity.

---

## Platform Notes (gotchas only)

### WordPress

- ONE SEO plugin, never both. 2026 recommendation: Rank Math for most sites (bigger free tier, ~3x smaller plugin); keep Yoast only on established sites already using it.
- Redirect attachment pages to parent posts (thin-URL factory otherwise).
- Permalinks `/%postname%/`; disable author archives on single-author sites; noindex thin tag pages.
- Plugin bloat is the usual CWV killer — caching plugin (WP Rocket/LiteSpeed) + image plugin (ShortPixel/Imagify WebP-AVIF) + CDN.

### Shopify

- Duplicate product URLs via collection paths: remove `| within: collection` from theme product links — the #1 Shopify SEO fix.
- No variant-level meta tags → metafields + Liquid customization.
- robots.txt control only via `robots.txt.liquid` (Shopify 2.0); no `.htaccess`/custom headers (use app or Cloudflare worker).
- Forced URL structure (`/products/`, `/collections/`) — accept and optimize within it.
- Apps each add JS → audit quarterly, lazy-load app scripts.
- Enhance default product schema via Liquid; add collection-page content below grid.

### Next.js (App Router)

- Metadata via `export const metadata` / `generateMetadata()`; canonical via `alternates.canonical`; `app/sitemap.ts` + `app/robots.ts`.
- JSON-LD as **server-rendered** `<script>` tags; use `<Image>` (auto WebP/lazy) but `fetchpriority="high"` and never `loading="lazy"` on the LCP image.
- Rendering: SSG for marketing/blog, ISR for products (e.g. revalidate 3600), SSR for search/filter pages, CSR only for authed dashboards.
- Verify with GSC URL Inspection "Live Test" that content is actually server-rendered; check metadata merging across nested layouts.

---

## Site Migration (highest-risk SEO event — read before ANY domain/platform/URL change)

Most migration traffic losses are preventable with preparation. Risk/recovery by type (internal benchmarks):

| Type | Risk | Recovery |
|---|---|---|
| HTTP→HTTPS | Low | 2-4 weeks |
| URL restructure (same domain) / CMS change (same URLs) | Medium | 4-8 weeks |
| Domain change (rebrand) / platform+URL change | High | 3-6 months |
| Domain+platform+URL / site merger | Very High | 6-12 months |

### Pre-migration (2-4 weeks before)

- [ ] Full crawl of old site (Screaming Frog): every URL, status, title, meta, canonical
- [ ] Export GSC indexed URLs + 16 months of Performance data + Links report; export backlinks (Ahrefs)
- [ ] Benchmark GA4 organic by page (12 months) + CWV + all structured data + hreflang
- [ ] For domain moves, verify all GSC variants/properties before launch: domain property,
      www/non-www, HTTP/HTTPS, and subdomains that are moving
- [ ] Build URL mapping spreadsheet: old URL → new URL, redirect type (301 always), monthly traffic, backlink count, priority (P0 = top 100 pages, P1 = top 1000, P2 = rest), status
- [ ] Mapping rules: 1:1 wherever possible; category-level redirects only as last resort; pattern/regex 301s for systematic changes; **no chains, no loops**
- [ ] Staging: robots.txt `Disallow: /` + noindex + password; crawl staging to validate redirects/canonicals/meta/schema/mobile/CWV

### Migration day (lowest-traffic window)

Launch sequence: (1) enable ALL redirects at once → (2) update canonicals → (3) update internal links → (4) update XML sitemap → (5) submit new sitemap to GSC → (6) update robots.txt → (7) verify HTTPS / no mixed content → (8) update hreflang → (9) verify structured data → (10) test homepage + top 20 + conversion pages.

For domain changes, use Search Console's Change of Address tool for all moved domain variants,
including subdomains and www/non-www variants. It is not a substitute for complete 301 redirects
or a same-domain URL-change process.

**Do NOT:** remove old sitemaps from GSC (Google needs them to discover redirects); block Googlebot; launch mid-core-update; remove redirects within the first year.

### Post-migration monitoring

- First 48h (critical): crawl old URLs — all redirects work; GSC Coverage — no 404s on key pages; SSL, mobile rendering, CWV, Rich Results Test, sitemap accepted.
- First 2 weeks (daily): a 10-20% traffic dip is normal; **>30% sustained drop = red flag**. Zero crawl activity, massive index drop, redirect chains = investigate immediately.
- First 30 days: verify backlink sources reach new URLs (catch 302s masquerading as 301s); update external links (social profiles, directories).
- 90 days: traffic should be at or above baseline; check for orphaned pages; verify all old URLs still redirect.

### Top failure causes (internal benchmarks)

| Failure | Prevention |
|---|---|
| Incomplete redirect map | Crawl old site completely; map every URL |
| 302 instead of 301 | Audit redirect type — link equity does not transfer on 302 |
| Redirect chains | Old URL → final URL directly, no intermediaries |
| Staging robots.txt / noindex shipped to prod | Search for `Disallow: /` and noindex across all templates before launch |
| Broken internal links | Update all internal links to new URLs |
| CWV regression on new platform | Performance-test before AND after |
| Lost structured data / hreflang | Migrate all schema + hreflang annotations |

### Redirect lifetime

URL restructure: 1 year minimum. Domain change: 2+ years (ideally permanent). HTTPS migration, page consolidation, high-backlink pages: permanent. Audit: weekly (month 1) → monthly (months 2-6) → quarterly.

2026 addition: preserve entity continuity (schema, sameAs, Wikidata) and migrate ALL structured data — AI systems rely heavily on it for citations.

---

## Accessibility, Security, and UX Signals

### Accessibility → traffic impact (internal benchmarks)

Not a direct ranking factor, but WCAG-compliant sites (internal benchmarks): +23% organic traffic, +27% additional keywords ranked, +22% session duration, -18% bounce rate, +15% conversion — because accessibility work overlaps SEO work (semantic HTML, heading hierarchy, alt text, descriptive links, captions/transcripts, mobile responsiveness, speed).

Checklist floor: semantic elements (`<header>/<main>/<article>/<nav>/<footer>` — no div soup), one H1 + logical H2-H6, alt text on informational images, no "click here" links, 4.5:1 contrast (WCAG 2.1 AA), 16px min body font, `lang` on `<html>`, labeled forms, visible focus, skip link. Compliance deadlines: EAA June 28 2025 (EU); ADA Title II April 24 2026 (US gov >50K population); WCAG 2.1 AA is the de facto target.

### Intrusive interstitials

| Penalized | Acceptable |
|---|---|
| Full-screen popups on mobile entry from search | Age verification gates |
| Standalone interstitials before content loads | Cookie consent (legally required) |
| Popups covering above-fold content; app-install interstitials | Login walls on genuinely private content; banners using <15% of screen |

Delay promos until scroll or 30+ seconds; exit-intent is generally acceptable; prefer slide-ins/bottom bars over centered overlays.

### Content syndication canonicals

| Approach | Safety |
|---|---|
| Partner adds `noindex` on the copy | Safest (Google recommended) |
| Partner adds cross-domain canonical to your original | Good |
| No attribution | Dangerous — you lose 40% potential traffic within first week (internal benchmark) |

Rules: publish on your site FIRST, submit to GSC URL Inspection immediately, wait 24-48h for indexing before syndicating, cap at 2-3 partners. Higher-authority partners can get indexed first and be treated as the original.

### Social + CRO notes

- Social signals: not a direct ranking factor. Highest indirect value: Reddit (direct Google ranking, #2 visibility after Wikipedia — internal benchmark; AI training data), LinkedIn (B2B), YouTube.
- CRO/SEO shared levers: CWV, mobile UX, clear CTAs, trust signals. Benchmark: every 100ms delay = -7% conversions. Serve universal content to bots + personalize client-side; canonical-control A/B variants.

---

## Industry / YMYL Specifics

YMYL (health, finance, legal — content affecting health, financial stability, or safety) gets the strictest E-E-A-T scrutiny. **Credentialed authorship is the non-negotiable across all of them.** Core-update impact data and the general YMYL E-E-A-T floor: on-page-and-content.md, YMYL Requirements.

| Vertical | Author requirement | Key extras |
|---|---|---|
| **Healthcare** | Written or reviewed by a licensed healthcare professional; visible "Medically reviewed by [Dr. Name]" + date | Cite peer-reviewed/NIH/Mayo/WHO; medical disclaimer; HIPAA-safe testimonials; MedicalWebPage/MedicalCondition/Physician schema. AI-assisted medical content is high-risk unless credentialed experts own accuracy, sources, and review |
| **Finance** | CFP / CFA / CPA or equivalent | SEC/FCA/ASIC compliance + legal review of claims; quarterly accuracy audits (rates/tax laws decay); risk disclaimers; FinancialProduct/BankAccount/LoanOrCredit schema; trust badges (FDIC, registration numbers) |
| **Legal** | Licensed attorneys with bar numbers | Jurisdiction-specific content (laws vary by state); "not legal advice" disclaimers; no-privilege notice on contact forms; LegalService/Attorney schema. Benchmark: 96% of legal-advice seekers use a search engine; legal SEO is overwhelmingly local |
| **Real estate** | — | IDX listings: canonical to original source + add unique neighborhood context; auto-redirect sold/expired listings to category pages; market reports need quarterly freshness |
| **Travel** | — | Hreflang essential (multi-language/currency); image SEO critical; plan seasonal content 3-6 months ahead; AI Overviews heavily target travel queries |

Cross-YMYL floor: named credentialed authors, citations to government/academic sources, quarterly accuracy audits for data-dependent content, industry disclaimers, transparent editorial-process page, real contact info (address/phone/email), industry-specific schema subtypes.

---

## Explicit / Adult Content

Use Google's explicit-content guidance when a site has sexually explicit or graphic violent
material, or when a borderline site is incorrectly filtered by SafeSearch.

- Keep explicit and non-explicit sections separated where possible; otherwise SafeSearch may treat
  a broader section or whole site as explicit.
- Allow Googlebot to crawl without an age gate for indexable public content; blocking the crawler
  prevents Google from classifying the page correctly.
- Add `meta name="rating" content="adult"` or the equivalent HTTP header only to sexually explicit
  pages. Over-applying adult metadata filters non-explicit pages.
- For explicit videos, use the video sitemap `family_friendly` signal correctly; don't mark
  non-explicit videos as not family-friendly.
- If incorrectly flagged, test with SafeSearch on/off, fix overbroad adult/video labels, and expect
  classifier reprocessing to take months.

---
