# On-Page and Content Reference

Actionable core for on-page optimization, E-E-A-T, topical authority, and content operations on any site. Gate and recipes: SKILL.md.

## Doctrine (applies to every section below)

- Natural language over keyword density. Google uses semantic understanding, not keyword counting — there is no magic density number.
- Over-optimization is penalized harder than under-optimization. Keyword stuffing, exact-match anchor saturation, boilerplate titles, and coverage-inventory writing all read as manipulation.
- Entities and keywords appear where a reader needs them — title, H1, first 100 words, headings that genuinely describe sections — never as a checklist of terms to inject.
- When in doubt, leave it out.
- Text relevance (query-to-content match) has the strongest ranking correlation at 0.47 — beating domain authority, backlinks, and page speed (2025 data). Matching the query beats decorating the page.

## Title Tags

| Attribute | Practice |
|---|---|
| Length | 50-60 characters (Google truncates at ~600px display width) |
| Primary phrase | Use one natural query/topic phrase the way a person would say it; place it early only when that still reads like a real title |
| Uniqueness | Unique title per page |
| Modifiers | Year ("2026"), "guide", "best", "how to" only when they accurately describe the page |
| Branding | Site name at end, separated by ` \| ` or ` - ` |
| Accuracy | Must describe actual page content |
| CTR triggers | Concrete differentiators, tested counts, dates, or scope statements that are true |
| Avoid | Keyword stuffing, ALL CAPS, misleading titles |

Google rewrites ~36% of titles — triggered by too long/short, excessive keywords, content mismatch, boilerplate patterns, or excessive branding. Compelling accurate titles reduce rewrites.

## Meta Descriptions

| Attribute | Practice |
|---|---|
| Length | 150-160 chars desktop, 120 chars mobile |
| Content | One-sentence pitch of what the reader gets + CTA; naming the topic naturally is enough (matching terms bold in the SERP as a side effect, never the goal) |
| Voice | Active voice, clear call-to-action, value proposition |
| Uniqueness | Unique per page |

Google rewrites ~63% of descriptions — write custom ones anyway. When displayed, custom descriptions lift CTR by 5.8%; Google's auto-pulled text is usually less compelling.

## Heading Structure

- One H1 per page, above the fold, naming the page's primary topic in natural language and
  clearly stating what the page delivers. May be longer/more descriptive than the `<title>`.
- Hierarchy: H1 primary topic → H2 major sections → H3 subsections → H4 detail. Never skip levels (H2 → H4).
- Write the outline from user questions and tasks FIRST, then check which queries it naturally serves. Headings should read as a table-of-contents outline; keywords land in H2/H3 only where the heading genuinely describes the section. Never generate headings from the keyword list (SKILL.md gate).
- 2026: clear heading hierarchies are how AI systems (AI Overviews, ChatGPT) extract and cite content.

## Keyword Placement and Intent

### Placement priority

| Location | Impact |
|---|---|
| Title tag | Highest — one natural primary phrase + concrete differentiator |
| H1 | High — primary topic, natural phrasing |
| First section | High — establish relevance and usefulness early |
| URL | Medium — short, descriptive, stable slug |
| H2/H3 headings | Medium — where the user-need outline naturally carries them |
| Body | Medium — natural density, semantic variations |
| Image alt text | Low-Medium — descriptive, keyword only where relevant |
| Meta description | Low (indirect) — SERP bolding, CTR |

Instead of density: semantic variations and related terms; entity coverage (related concepts/people/places Google associates with the topic); complete coverage of subtopics a user would expect. All of this in service of the reader — see Doctrine.

### Search intent alignment

| Intent | SERP pattern | Content type |
|---|---|---|
| Informational | Featured snippets, knowledge panels, PAA | Guides, tutorials, FAQs, blog posts |
| Navigational | Brand sitelinks, direct URL | Homepage, product, about |
| Transactional | Shopping results, ads, product carousels | Product, pricing, comparison pages |
| Commercial investigation | Reviews, comparisons, "best of" lists | Comparison articles, reviews, buying guides |

Critical: match content TYPE to the dominant SERP pattern. If Google shows product pages for a query, a blog post won't rank (and vice versa).

## Internal Linking and Anchors

| Principle | Detail |
|---|---|
| Flat architecture | Key pages within 3 clicks of homepage |
| Equity flow | Homepage/top pages hold most authority; link strategically to channel it to deeper content |
| Topic clusters | Pillar ↔ cluster bidirectional linking |
| No orphans | Every indexable page needs ≥1 internal link (~40% of internal link value is wasted on poorly structured sites with orphaned pages) |
| Placement | Contextual body links > sidebar/footer/nav links (body links pass more equity) |
| Volume | 2-5 contextual links per 1,000 words; total page links under 150 |

A strategic internal link from a high-authority page provides more ranking boost than a low-quality external backlink.

### Anchor text mix

Diagnostic ranges, not quotas — a natural profile lands here on its own; never engineer anchors toward these numbers (same rule as external anchors, authority-and-offpage.md).

| Type | Example | Share |
|---|---|---|
| Partial match | "technical SEO best practices" | Primary approach (30-40%) |
| Natural/long-tail | "this guide covers everything about..." | 20-30% |
| Exact match | "technical SEO" | Sparingly (10-20%) — exact-match saturation is over-optimization |
| Branded | "according to Moz" | 10-15% |
| Generic | "click here", "learn more" | Minimize; no semantic value |

## Image Optimization

Google Images delivers 22.6% of all web traffic — image SEO is not optional for content-heavy sites.

| Format | Notes |
|---|---|
| AVIF | 50% smaller than JPEG; 90%+ browser support (2025); primary photo format |
| WebP | 25-35% smaller than JPEG; 98%+ support; AVIF fallback |
| JPEG | Legacy fallback |
| PNG | Lossless, transparency graphics |
| SVG | Icons, logos, simple illustrations |

Serve via `<picture>` with AVIF → WebP → JPEG fallback.

### Alt text

| Do | Don't |
|---|---|
| Describe the image accurately, ≤125 chars | Keyword-stuff ("best SEO tips SEO guide SEO tools") |
| Include keywords only when naturally relevant | Start with "Image of"/"Picture of" |
| `alt=""` for decorative images only | Leave empty on informational images |
| Write as if for a visually impaired user | Use the filename or duplicate surrounding text |

### Checklist

- [ ] Descriptive filenames (`blue-running-shoes.webp`, not `IMG_4832.webp`)
- [ ] Explicit `width`/`height` (prevents CLS)
- [ ] Compress: <200KB most images, <100KB thumbnails
- [ ] `srcset` responsive variants; CDN delivery
- [ ] Images in XML sitemap (or dedicated image sitemap)
- [ ] Below-fold images: `loading="lazy"`
- [ ] LCP image: NEVER lazy-load — eager + `fetchpriority="high"` (lazy-loading the LCP image is one of the most common 2026 audit regressions)

## E-E-A-T

Content quality is the #1 ranking factor at 23% weight (First Page Sage 2025). Trustworthiness is the center — Experience, Expertise, and Authoritativeness all build toward it.

| Component | Question | Evaluated via |
|---|---|---|
| Experience | Has the author actually done/used/lived this? | First-person accounts, original photos, process documentation, real examples |
| Expertise | Knowledge or credentials? | Author bios, credentials, publication history, cited sources |
| Authoritativeness | Recognized in the field? | Backlinks from authoritative sites, brand mentions, industry recognition |
| Trustworthiness | Accurate, transparent, safe? | HTTPS, contact info, editorial policies, accuracy, citations, privacy policy |

### Implementation signals (site-level checklist)

| Signal | Implementation |
|---|---|
| Author pages | Dedicated `/author/name/` with bio, credentials, published-work links |
| Author schema | `Person` schema with `sameAs` links to LinkedIn/Twitter/professional profiles |
| About page | Who runs the site, editorial mission, team credentials |
| Editorial policy | How content is created, fact-checked, updated |
| Contact info | Real address, phone, email (especially YMYL) |
| Source citations | Link to primary sources, studies, official docs |
| Original research | Proprietary data, surveys, case studies, experiments |
| Process documentation | Show the work: screenshots, methodology, original photos |
| Update dates | Visible "last updated"; content freshness = 6% ranking factor |
| User-generated proof | Comments, testimonials, community validation |

### Scrutiny by category

| Category | Scrutiny | Required |
|---|---|---|
| YMYL (health, finance, legal, safety) | Highest | Professional credentials, cited medical/legal sources, peer review |
| Product reviews | High | Hands-on-use evidence, original photos/video, specifics |
| News/journalism | High | Bylines, editorial standards, fact-checking process |
| Technical tutorials | Medium-High | Demonstrated expertise, working code, error handling |
| Entertainment/lifestyle | Medium | Consistent voice, real experience, community engagement |
| Satire/opinion | Lower | Clearly labeled as opinion |

2026 context: Google's March 2025 core update hit YMYL sites hardest where firsthand experience was missing; amid AI-content flooding, algorithms actively reward demonstrated first-hand experience.

## YMYL Requirements

Categories: health & safety, financial, legal, news/current events, groups of people, major-purchase shopping, government/civics.

- Strictest E-E-A-T scrutiny of any content type. Credentials matter: content written or reviewed by qualified professionals, with clear attribution.
- December 2025 core update impact: affiliate/review sites 71% affected, health/medical 67%, e-commerce 52%.
- Per-vertical author-credential requirements (healthcare, finance, legal, real estate, travel): specialized.md, Industry / YMYL Specifics.

## Topical Authority and Content Clusters

Niche expertise = 13% of ranking weight (First Page Sage). Built through systematic topic coverage, pillar → cluster.

| | Pillar page | Cluster page |
|---|---|---|
| Length | 3,000-5,000 words, comprehensive | 1,500-3,000 words, depth over breadth |
| Scope | Full topic at high level; the site's definitive page | One specific subtopic |
| Linking | Links to EVERY cluster page | Back to pillar + related clusters |
| Target intent | Head topic | Long-tail/subtopic intent; match the job the searcher is trying to complete |
| Updates | Refresh quarterly (data, examples, links) | As needed per freshness table below |

Impact data (all four are Apr 2026 internal-benchmark figures, none re-confirmed mid-2026 — directional only): +40% organic traffic from clusters vs non-clustered strategies; 3x faster ranking gains vs link-acquisition-only; +23% organic visibility for established clusters (June 2025 core update); AI citation rate 12% → 41% for pillar-organized topics (see ai-search-geo.md ledger for that one specifically).

## Freshness, Decay, and Cannibalization

Freshness signal: annual updates = +4.6 positions average; visible "last updated" dates; freshness = 6% ranking factor.

| Content type | Update frequency | What to update |
|---|---|---|
| Statistics/data posts | Quarterly | Numbers, sources, charts |
| Technology guides | Semi-annually | Tools, versions, screenshots |
| Strategy/best practices | Annually | Tactics, examples, case studies |
| Evergreen reference | When factually outdated | Core facts, links |
| News/trends | Replace, don't refresh | Archive old, publish new |

- **Decay detection**: compare trailing-30-day traffic to the 30-day peak. Flag pages below 50% of peak sustained 60+ days → update or consolidation candidates.
- **Cannibalization detection**: from GSC, find pages ranking for the same query in positions 5-15 with >100 monthly impressions. Consolidate into one strong page, 301 the other.
- **Pruning decision** (for flagged pages, in order): **improve** (real demand + salvageable page)
  → **consolidate + 301** (overlapping intent with a stronger sibling) → **noindex** (users need
  it, search never will) → **410** (no users, no links). Never 404/410 a URL with backlinks:
  301 it to the closest surviving equivalent. Pruning matters because the Helpful Content
  classifier is site-level: dead weight drags every other page.

## Content Workflow

### Pre-write
1. Audience/use-case boundary — who needs this, what decision/task are they completing, and why
   this site has standing to answer
2. Topic/intent research — primary phrase, related terms, user questions, and entities that
   genuinely matter to the answer; the page's target cluster comes from the query→page map
   (keyword-strategy.md), never ad hoc
3. SERP analysis — top 10 for intent, format, depth
4. Information-gain requirement — name the original data, first-hand evidence, expert input,
   screenshots, testing, template, calculator, local knowledge, or decision framework this page
   adds beyond the SERP
5. Content gap analysis — what competitors cover that readers genuinely need and you don't
6. Outline — H2/H3 structure covering the reader journey, not a query list

### Write
1. Hook in first paragraph — answer the query or promise value immediately
2. Primary phrase in the first section, naturally, if it fits the sentence
3. Structured format — tables, lists, code blocks, FAQs for scannability
4. Original value — unique data, expert quotes, personal experience
5. Address "People Also Ask" questions inline
6. Multimedia — original images, diagrams, video (video increases dwell time)

### Post-write
1. Internal links — 2-5 contextual per 1,000 words to related content
2. External citations — authoritative sources (studies, official docs)
3. Schema — Article plus the entity graph as appropriate (FAQ/HowTo rich results are retired — May 2026 / 2023; see structured-data.md)
4. Meta — title tag, meta description, URL
5. Images — alt text, compression, formats

NLP/coverage tools (Surfer, Clearscope, MarketMuse, etc.) can score topical coverage vs SERP competitors and surface missing subtopics/entities — use them to find what a reader would expect and is missing, never as a term-injection list (Doctrine applies).

### Content quality score (pre-publish / manual audit)

Scores inherent content quality; the analytics-driven post-publish counterpart is the Content
Performance Score in measurement-and-audit.md — keep the two distinct, never blend them.

```
quality_score = completeness(0.10) + topical_coverage(0.25) + originality(0.20)
              + engagement(0.20) + eeat(0.15) + technical(0.10)
```

Scoring basis per component: checklist percentage for E-E-A-T and technical (signals present /
signals applicable), NLP-tool coverage percentage for topical coverage, site-analytics
percentile for engagement, and a fixed reviewer rubric for completeness and originality; state
the basis used when reporting the score.

| Component | Target |
|---|---|
| Completeness | Comparable depth to the SERP because the needed subtopics are covered, not because the word count was padded |
| Topical coverage | >80% of target entities (NLP tool score) |
| Originality | >50% original value-add |
| Engagement | Scroll depth / time on page / return rate above site average (behavioral signals = 12% ranking weight) |
| E-E-A-T | All implementation signals present |
| Technical | Schema, images, headings, internal links optimized |

## Publishing Cadence

| Site stage | Cadence | Notes |
|---|---|---|
| New blog (0-6 months) | 6-8 posts/month | Build topical foundation quickly |
| Growing (6-18 months) | 4-6 posts/month | Steady growth + some updates |
| Established (18+ months) | 2-4 posts/month + updates | Quality over quantity; refresh evergreen |
| Enterprise | Daily+ with editorial team | Multiple content streams |

- Consistency beats volume: 4 posts/month for 12 months > 48 posts in month 1 then nothing.
- Allocate ~30% of effort to updating existing content; "frequency" in 2026 = new content + substantive refreshes.
- Diminishing returns: >2 posts/week without maintenance leads to content decay. Erratic or low-quality publishing hurts more than infrequent excellence.
- Monthly rhythm: wk1 new pillar/cluster post → wk2 refresh 1-2 top evergreen posts → wk3 new post → wk4 audit + gap-fill or consolidation.
