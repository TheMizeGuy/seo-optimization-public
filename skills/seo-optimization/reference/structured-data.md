# Structured Data (JSON-LD) — Implementation Reference

Purpose: how to implement, link, validate, and win rich results with schema markup on an arbitrary site — plus featured snippet / PAA / Discover optimization that pairs with it.

## Hard doctrine (non-negotiable)

| Rule | Why |
|---|---|
| Schema must mirror visible page content exactly | Mismatched markup is a manual-action category (Google policy) |
| Mark up only what the page really is | Schema must reflect the visible page and its main focus; don't add types just because they used to produce a rich result |
| Real data only | No fabricated ratings/reviews; self-serving reviews (author reviews own product) are a trust violation. Google actively monitors for self-review and non-user-submitted content marked as reviews. Since Jul 24, 2026 the review-snippet guideline also bans fake reviews and undisclosed incentivized reviews (paid, discounted, free product) on the page or in markup — incentivized reviews are allowed only with clear, prominent disclosure; violation is a structured-data manual action that strips rich-result eligibility |
| More types is not more eligibility | Be specific — use the most detailed applicable type; don't stack types hoping for extra rich results |
| Never mark up hidden content | Policy violation; only content visible to readers |
| No deception | Don't use schema to mislead users about what the page contains |

## Why this matters (impact data, source-labeled)

| Metric | Value | Source |
|---|---|---|
| Rich snippet CTR increase | 20-35% vs standard results | Industry studies |
| Nestle: rich result vs non-rich | 82% higher CTR | Google case study (pre-2020 — dated, directional) |
| Schema and AI features | Google states structured data is NOT required for AI Overviews/AI Mode (official, May 2026). Schema still aids entity corroboration and machine understanding — implement for the entity graph, never as an "AI visibility" trick | Google Search Central, May 2026 |

## Format: prefer JSON-LD

Google supports JSON-LD, Microdata, and RDFa when valid, but recommends JSON-LD because it is
easier to implement and maintain: separation from HTML, dynamic/server-side generation, and
multi-type pages via an array or `@graph`. Use JSON-LD for new work unless an existing platform
already emits clean Microdata/RDFa.

### Server-side generation (best practice)

Generate JSON-LD server-side into the raw HTML before it reaches the browser — Googlebot sees it without rendering.

| Stack | Approach |
|---|---|
| Next.js (App Router) | Plain `<script type="application/ld+json">` via `dangerouslySetInnerHTML={{ __html: JSON.stringify(data) }}` in the page/layout component (server-rendered into initial HTML). NOT `generateMetadata()` (the Metadata API has no JSON-LD field) and not `next/script` (that component is for loading external scripts) |
| WordPress | Yoast SEO, Rank Math, or Schema Pro |
| Shopify | Built-in product schema; extend via apps or theme code |
| Custom | Template engine renders JSON-LD from database/API data (also fixes stale prices/availability — dynamic generation from live data source) |

## Schema type selection by page type

### Universal baseline (every site)

| Type | Rich result | Priority |
|---|---|---|
| Organization | Knowledge panel, logo, social profiles | Required for every site |
| WebSite | Sitelinks search box no longer appears as a Google rich result; type still valid for the entity graph | Required for every site |
| WebPage | Basic page identification | Foundational |
| BreadcrumbList | Breadcrumb trail in SERPs | Required for navigation |
| Article / BlogPosting | Article rich result with author, date | Required for content sites |
| FAQPage | **None — FAQ rich results retired May 7, 2026** (tooling/reporting removed through Aug 2026) | Optional only for real visible FAQ sections; never add "for rich results" |

### Content-specific

| Type | Rich result | When |
|---|---|---|
| HowTo | None in Google Search — HowTo rich results are retired | Only if the visible page is genuinely step-by-step and downstream systems need it |
| Recipe | Rich recipe card with ratings, time | Food/cooking content |
| Product | Price, availability, reviews | E-commerce |
| Review / AggregateRating | Star ratings in SERPs | Review content (genuine third-party reviews) |
| Event | Date, location, tickets | Event listings |
| VideoObject | Video thumbnail in SERPs | Pages with embedded video |
| LocalBusiness | Business info in local pack | Physical businesses |
| JobPosting | Google Jobs listing | Job listings |
| Course | Course list rich result | Educational content — needs at least three courses marked up plus Carousel markup on a summary or all-in-one page (Course doc, Jul 4, 2026); a single course page cannot earn it |
| SoftwareApplication | App info, ratings | App/software pages |

### E-E-A-T supporting

| Type/property | Purpose |
|---|---|
| Person (author) | Links author to credentials, profiles, published work |
| sameAs | Connects entity to verified profiles (LinkedIn, Wikipedia, etc.) |
| Organization + `foundingDate`, `numberOfEmployees` | Establishes authority |
| MedicalWebPage / FinancialProduct | YMYL-specific trust signals |

## Active Google rich-result eligibility (practical minimums)

Practical minimums for a useful rich result — verify against the current Google feature guide
before shipping; Google's required/recommended split changes, and several fields below are
recommended-not-required (omitting them narrows the result, it doesn't always suppress it).

| Type | Rich result | Practical minimum |
|---|---|---|
| Article | Author, date, image in SERP | headline, image, author, datePublished (all *recommended* per Google — no hard-required fields; a bare Article still qualifies but renders thin) |
| Product | Price, availability, rating stars | name + at least one of offers / review / aggregateRating (offers needs price + availability for the shopping treatment) |
| Recipe | Cook time, calories, rating | name, image (required); recipeIngredient/times strongly recommended for the full card |
| Event | Date, location, ticket info | name, startDate, location |
| Video | Video thumbnail | name, description, thumbnailUrl, uploadDate |
| LocalBusiness | Business info in local results | name, address, telephone |
| BreadcrumbList | Breadcrumb trail | itemListElement with position, name |
| Review | Star ratings | reviewRating, author |

Missing genuinely-required properties = feature ineligible (Rich Results Test flags them as
errors; missing recommended fields appear as warnings). Always check schema.org for vocabulary
and Google Search Central's feature docs for Google Search behavior; schema.org validity alone
does not mean Google shows a rich result.

### Situational Google feature guides — load only when the page qualifies

The table above covers the common cases. Google Search also supports niche feature guides that
should not bloat ordinary pages, but must be considered when the site actually has that content
type:

| Feature family | Use when | Guardrail |
|---|---|---|
| Course list / Education Q&A / Math solver | Education providers, flashcards, step-by-step math solving | Mark up only the visible educational interaction; don't use generic Q&A markup for ordinary FAQs |
| Discussion forum / Profile page / Q&A | Forums, community threads, creator/profile pages, answer sites | Pick the guide that matches the visible page type; UGC spam moderation matters as much as markup |
| Employer aggregate rating / JobPosting | Hiring organizations and job listings | Use real employer/job data; stale or misleading listings create policy risk |
| Image metadata | Image-heavy sites, licensing/credit workflows, publishers | Add creator/license/credit data only when accurate and visible or otherwise verifiable |
| Movie / Carousel / Vacation rental | Entertainment, list/carousel, lodging inventory | Use only for real inventory/list pages; don't convert thin affiliate pages into "rich-result" pages |
| Subscription and paywalled content | Publishers/memberships with gated content | Pair with Flexible Sampling and paywall markup so Google can distinguish paywalls from cloaking |
| SoftwareApplication | Apps and software product pages | Ratings/pricing must reflect the visible app listing, not marketing claims |
| Aggregator unit / Supplier unit (EEA only) | Vertical search services (OTAs, comparison shopping, directories) as aggregators; direct providers (hotels, airlines, local businesses, service providers) as suppliers — extended to local-business queries Sep 18, 2026 | No structured data or Merchant Center needed beyond crawlable pages; aggregators need Vertical Search Service approval; see Google's "Regional differences in Search experience" doc (Sep 8, 2026) |

Fact check / ClaimReview and Book actions are gated or legacy, not ordinary situational wins —
see the retired/limited table below for their current status.

For these situational types, load Google's current feature guide at implementation time. Rich
Results Test support and Search Console reporting can change faster than schema.org vocabulary.

### Retired, limited, or phasing-out traps — do not implement blindly for Google rich results

| Type | Status |
|---|---|
| **FAQ** | **Rich results fully retired May 7, 2026** (restricted to authoritative sites since 2023; GSC reporting removed June 2026) |
| HowTo | Rich results deprecated since 2023 |
| Practice Problem | Deprecated — no rich results |
| Dataset | Not a Google Search rich-result feature; Dataset markup is for Dataset Search/other consumers |
| Sitelinks Search Box | No longer shown in Google Search; Google decides sitelinks automatically |
| Course Info / Estimated Salary / Learning Video / SpecialAnnouncement / Vehicle Listing | Removed from Google Search rich-result documentation in 2025; do not add for eligibility |
| ClaimReview / Fact check | Google Search support is phasing out; Fact Check Explorer still supports the markup. Treat as legacy/specialized, not a general rich-result target |
| Book actions | Not deprecated, but limited/onboarding-gated for book providers with wide inventory and feed review; do not add to ordinary article/product pages |

No ranking penalty for keeping deprecated schema; it just won't generate rich results anymore. The
Search Gallery can retain legacy or limited feature guides, so the current Google feature guide
wins over local summaries.

### New/evolved types (2025-2026)

| Type | Status |
|---|---|
| Speakable | Advanced/limited; only use when the page truly has speakable news-style passages |
| Product variants | New in 2025 — color/size/version variations for e-commerce |
| Merchant listing | Expanded — free product listings in Google Shopping |
| Merchant return/shipping/loyalty policies | Useful for e-commerce eligibility and Merchant Center consistency. Put the general return policy on `Organization.hasMerchantReturnPolicy`; an Offer-level `MerchantReturnPolicy` supports fewer properties and is for per-product overrides (return-policy doc, Sep 8, 2026) |
| Product adult consideration | `hasAdultConsideration` added to Merchant listing and Product variant docs in May 2026 for parity with Merchant Center adult-product signals |
| Organization structured data | Updated guidelines — expanded attributes for entity recognition |

## @id entity linking and the site-wide entity graph

`@id` gives entities unique persistent identifiers so schema blocks form a connected graph instead of isolated islands. Google resolves `@id` references across blocks on the same page. The value is a URI reference (does not need to resolve); convention is `https://domain.com/#type`.

### @id naming conventions

| Entity | Pattern |
|---|---|
| Organization | `https://example.com/#organization` |
| WebSite | `https://example.com/#website` |
| Person (author) | `https://example.com/#person-firstname-lastname` |
| Article | `https://example.com/article-slug/#article` |
| Product | `https://example.com/product-slug/#product` |
| LocalBusiness | `https://example.com/#localbusiness` |
| BreadcrumbList | `https://example.com/page/#breadcrumb` |

### Key linking properties

| Property | Meaning | Usage |
|---|---|---|
| `mainEntityOfPage` | "This entity is the primary topic of this page" | On every content page; links content entity to its WebPage |
| `about` | Primary topics of the content | Stronger than `mentions`; add `sameAs` to Wikipedia/Wikidata on each Thing |
| `mentions` | Entities referenced but not the primary topic | Secondary entities |
| `sameAs` | Links entity to verified external profiles | Critical for entity recognition — Wikidata and Wikipedia sameAs links are the strongest entity signals |
| `isPartOf` | Hierarchical containment | WebPage → WebSite |

### Nesting vs flat vs hybrid

| Pattern | Best for |
|---|---|
| Nested (everything inline) | Simple one-off entities (small publisher block, single offer) |
| Flat + @id (separate blocks linked by ID) | Entities referenced on multiple pages (authors, organization) |
| Hybrid (nest simple, @id complex/reused) | Most real-world implementations |

Define the author Person once, reference by `@id` on every article.

### Canonical @graph example (article page with full entity graph)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://example.com/#organization",
      "name": "Company Name",
      "url": "https://example.com",
      "logo": "https://example.com/logo.png",
      "sameAs": [
        "https://www.wikidata.org/wiki/Q12345678",
        "https://en.wikipedia.org/wiki/Company_Name",
        "https://linkedin.com/company/x"
      ]
    },
    {
      "@type": "WebSite",
      "@id": "https://example.com/#website",
      "url": "https://example.com",
      "name": "Site Name",
      "publisher": { "@id": "https://example.com/#organization" }
    },
    {
      "@type": "WebPage",
      "@id": "https://example.com/seo-guide/#webpage",
      "url": "https://example.com/seo-guide/",
      "name": "Page Title",
      "isPartOf": { "@id": "https://example.com/#website" },
      "breadcrumb": { "@id": "https://example.com/seo-guide/#breadcrumb" }
    },
    {
      "@type": "BreadcrumbList",
      "@id": "https://example.com/seo-guide/#breadcrumb",
      "itemListElement": [
        { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://example.com/" },
        { "@type": "ListItem", "position": 2, "name": "SEO", "item": "https://example.com/seo/" },
        { "@type": "ListItem", "position": 3, "name": "Page Title" }
      ]
    },
    {
      "@type": "Person",
      "@id": "https://example.com/#person-john",
      "name": "John Smith",
      "url": "https://example.com/author/john-smith",
      "jobTitle": "Head of SEO",
      "worksFor": { "@id": "https://example.com/#organization" },
      "sameAs": ["https://linkedin.com/in/john-smith"],
      "knowsAbout": ["SEO", "Content Strategy"]
    },
    {
      "@type": "Article",
      "@id": "https://example.com/seo-guide/#article",
      "headline": "Complete SEO Guide",
      "author": { "@id": "https://example.com/#person-john" },
      "publisher": { "@id": "https://example.com/#organization" },
      "mainEntityOfPage": { "@id": "https://example.com/seo-guide/#webpage" },
      "datePublished": "2026-04-09",
      "dateModified": "2026-04-09",
      "image": "https://example.com/seo-guide.webp",
      "about": [
        { "@type": "Thing", "name": "SEO", "sameAs": "https://en.wikipedia.org/wiki/Search_engine_optimization" }
      ]
    }
  ]
}
</script>
```

### Speakable (advanced, AI citation)

Flag the most citable passage for voice assistants / AI synthesis via `speakable` on WebPage with `SpeakableSpecification` (`cssSelector` or `xpath`). Target concise self-contained passages (2-3 sentences max per selection) — definitions, key facts, direct answers. Be surgical, never whole articles; put your most unique insight in the speakable passage.

## Validation workflow

1. Write content that genuinely qualifies for the schema type.
2. Implement JSON-LD per schema.org spec (all required properties, ISO 8601 dates).
3. Test with **Google Rich Results Test** (search.google.com/test/rich-results) — rich-result eligibility.
4. Validate syntax with **Schema.org Validator** (validator.schema.org).
5. Monitor **GSC Enhancements report** for site-wide schema errors.
6. Check actual SERP appearance for target queries.

(Google Structured Data Markup Helper can generate initial markup.)

### Common errors

| Error | Impact | Fix |
|---|---|---|
| Missing required properties | Schema ignored | Add all required fields per schema.org spec |
| Schema doesn't match visible content | Manual action risk | Schema must reflect what users see |
| Marking up hidden content | Policy violation | Only visible content |
| Self-serving reviews | Trust violation | Genuine third-party reviews only |
| Incorrect nesting | Broken rich results | Validate with testing tools |
| Stale data (old prices/availability) | Poor UX | Generate dynamically from live data |

### Per-site checklist

- [ ] Every page: Organization + WebSite + WebPage + BreadcrumbList minimum
- [ ] Content pages add Article/Product/LocalBusiness as appropriate
- [ ] All entities use @id for cross-block references; keep @id values consistent across pages (aids entity corroboration — Google only confirms same-page resolution)
- [ ] Organization has sameAs to all verified profiles + Wikidata
- [ ] Authors defined as Person entities with credentials and sameAs
- [ ] mainEntityOfPage links content entities to their pages
- [ ] about/mentions declare topic entities with sameAs to Wikipedia/Wikidata
- [ ] ISO 8601 dates; all required properties present; validated; no hidden-content markup

## Featured snippets

Context (2026): featured snippet SERP visibility dropped 64% Jan-Jun 2025 (15.41% → 5.53%); Google usually shows AI Overviews OR featured snippets, rarely both. Still critical for voice search and for queries where AI Overviews don't appear. AI Overview trigger rates are tracker-dependent (25-50% of queries, 2026 measurements; the older "58%" figure is superseded) — current CTR dynamics live in `ai-search-geo.md`.

| Snippet type | Format | Best for |
|---|---|---|
| Paragraph | 40-60 word answer block | "What is", "Who is", definitions |
| Ordered list | Numbered steps | "How to", processes |
| Unordered list | Bullets | "Best of", "types of" |
| Table | Structured comparison | Comparisons, specifications |

Tactics: exact question as H2/H3; direct 40-60 word answer immediately after the heading, then elaborate; lists for processes, tables for comparisons; you must already rank top 10 (page 1) to win a snippet; target several related questions per page.

"Read more" deep links are a snippet-adjacent Search appearance. Improve the odds with clear
section anchors, descriptive headings, and self-contained passages; do not create fake jump links
or hidden anchor text just to chase the appearance.

## People Also Ask (PAA)

PAA reveals underserved intent, content gaps, long-tail ideas, and user-journey progression. It is evidence of genuine user questions — feed it into the content OUTLINE; never install PAA phrasing as a heading list (that is the query-mapped-architecture anti-pattern; SKILL.md gate applies). Optimization:

| Strategy | Implementation |
|---|---|
| Mine PAA for content ideas | Click through PAA chains 3-4 levels deep |
| Answer PAA questions the outline already covers | Direct visible answers where users genuinely have those questions |
| Concise answers | 40-60 words immediately after the relevant heading |
| No FAQPage markup needed | FAQ rich results retired May 2026 — the visible answers are what PAA and AI surfaces extract |

## Google Discover

Interest-based, not query-based — no keyword targeting. Mobile audience (Google app, Chrome mobile). Traffic pattern: sharp spikes fading within 48-72 hours. AI summaries covered ~51% of the feed as of Nov 2025 (industry estimate, unverified). Google shipped its first Discover-only core update Feb 5-27, 2026 (Search Central blog; English/US first, expansion promised) with three stated goals: more locally relevant content from in-country sites, less sensational/clickbait content, and more in-depth original content from sites with demonstrated expertise. Ordinary core updates also affect Discover. A Feb 2026 Discover collapse is that update, not a site-side regression.

Eligibility/optimization checklist:

- [ ] Images at least **1200px wide** (large images get significantly more clicks)
- [ ] `<meta name="robots" content="max-image-preview:large">` — without it content may appear with small or no image
- [ ] Mobile-optimized, fast-loading pages (CWV compliance)
- [ ] Compelling non-clickbait headlines
- [ ] E-E-A-T signals: author bios, credentials, citations
- [ ] Mix of timely and evergreen content; consistent publishing schedule
- [ ] Unique content with original perspectives
- [ ] Monitor via GSC Discover Performance report
