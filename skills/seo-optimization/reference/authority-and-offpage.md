# Authority and Off-Page SEO

Purpose: how to evaluate, build, and defend real domain authority — links, brand signals, and entity recognition — for any site an agent is optimizing.

## What Authority Actually Is

- Authority is domain-level. `siteAuthority` is a domain-level feature, confirmed by the 2024 Google API documentation leak. Individual pages inherit the domain's standing; a great page on a weak domain still competes from behind.
- Authority is earned, never manufactured. No paid links, no PBNs, no link exchanges — a link penalty on a small site is unrecoverable in practice.
- Link-quality mismatches actively demote (API leak): links that don't fit the site's real profile (topic, tier, traffic) aren't merely ignored — they can hurt.
- Brand mentions count even when unlinked. Google attributes unlinked brand mentions as trust signals.
- Weighting: backlinks = 13% of ranking weight (First Page Sage 2025, down from 15% in 2024). Quality over quantity is the dominant trend; brand signals and entity recognition are increasingly important for AI search visibility.

**Honesty framing for diagnosis:** when a site asks "why aren't we page 1," the majority of the gap is usually off-site — domain authority, entity recognition, brand presence — not a missing on-page tweak. Say so plainly; do not sell title-tag changes as the fix for an authority deficit. AI systems use entity confidence as a pre-filter before evaluating content at all: no entity recognition = no citations. The same honesty cuts the other way: authority explains head-term losses, not the absence of a non-branded plan — the mid/long-tail function queries in keyword-strategy.md stay winnable at current authority and are worked in parallel, never deferred until "authority is fixed."

## Link Quality Evaluation

| Factor | High value | Low value |
|--------|-----------|-----------|
| Source authority | Major news outlets, .edu, .gov, industry leaders | New blogs, PBNs, directories |
| Relevance | Topically related to your content | Random/unrelated sites |
| Placement | Within main editorial content | Footer, sidebar, comment |
| Anchor text | Natural, descriptive, contextual | Exact-match keyword spam |
| Link type | Editorial (earned through merit) | Paid, exchanged, manipulated |
| Traffic | Source page gets real traffic | Zero-traffic pages |
| Follow status | Dofollow | Nofollow (still some value but less) |
| Uniqueness | First link from this domain | Repeat links from same domain (diminishing returns) |

Link value hierarchy (best to worst):

1. Editorial links from high-authority, relevant sites (gold standard)
2. Digital PR coverage (news, features, expert quotes)
3. Niche industry resource pages and directories
4. Guest posts on relevant, quality sites
5. Social profiles and brand mentions
6. Forum/community participation (minimal direct value)
7. Comment links (near-zero value)

## Three-Tier Link Building Strategy

### Tier 1 — highest impact

| Strategy | Description | Effort | Value |
|----------|-------------|--------|-------|
| Digital PR | Newsworthy content (original research, data studies, industry reports) journalists link to | High | Very High |
| Original research & data | Surveys, case studies, proprietary data that become cited sources | High | Very High |
| Expert roundups / quotes | Become a quoted source via HARO, Connectively, journalist outreach | Medium | High |
| Linkable assets | Tools, calculators, interactive content, comprehensive guides | High | Very High |

### Tier 2 — sustained growth

| Strategy | Description | Effort | Value |
|----------|-------------|--------|-------|
| Guest posting | Quality articles on relevant authority sites | Medium | Medium-High |
| Broken link building | Find broken links on relevant sites, offer replacement | Medium | Medium |
| Resource page outreach | Get listed on curated niche resource pages | Medium | Medium |
| Niche edits | Editorial links placed within existing content on relevant sites | Low-Medium | Medium-High |
| Content partnerships | Co-create content with complementary brands | Medium | Medium |

### Tier 3 — supplementary

| Strategy | Description | Effort | Value |
|----------|-------------|--------|-------|
| Local citations | Business directories, chamber of commerce, local orgs | Low | Low-Medium |
| Industry directories | Niche directories with editorial review | Low | Low-Medium |
| Social profiles | Complete profiles on major platforms | Low | Low |
| Podcast appearances | Guest spots (link in show notes) | Medium | Medium |

### Never do (2026 spam policies)

| Tactic | Risk |
|--------|------|
| Paid links without `rel="sponsored"` | Manual action |
| Link exchange schemes | Devaluation or penalty |
| Private blog networks (PBNs) | Severe link-spam risk; do not label as a named 2026 update target unless Google explicitly says so |
| Widget/embed link schemes | Devaluation |
| Mass directory submissions | Waste of time |
| Forum/comment spam | No value; may trigger spam filters |
| Article spinning / syndication networks | Penalty risk |
| Expired domain acquisition for link redirection | March 2024 spam policy target |

## Digital PR and Original-Data Linkbait

The Tier 1 engine in practice: publish something only you can publish, then pitch it.

- Original research (surveys, proprietary datasets, industry reports) becomes the cited source other sites must link to — the only link tactic that compounds.
- Data studies and statistics pages attract passive links for years; keep them updated so citations refresh.
- Free tools and calculators are permanent linkable assets; one strong tool outperforms dozens of guest posts.
- Expert-quote pipelines (HARO/Connectively, direct journalist relationships) convert expertise into recurring editorial links and brand mentions.

## Anchor-Text Distribution — Smell Detector, Not Quota

Use this table to DIAGNOSE an unnatural profile. Never engineer anchors toward these numbers — a natural profile lands here on its own; a manufactured one gets filtered.

| Anchor type | Natural share of profile | Example |
|-------------|-------------------------|---------|
| Branded | 30-40% | "Acme Corp", "acme.com" |
| Naked URL | 15-20% | "https://www.acme.com/page" |
| Natural/long-tail | 15-20% | "this comprehensive guide on SEO" |
| Partial match | 10-15% | "SEO best practices guide by Acme" |
| Exact match | 5-10% | "SEO best practices" |
| Generic | 5-10% | "click here", "learn more", "this article" |

Over-optimized profiles (too many exact-match anchors) trigger Google's link spam filters. Exact-match share well above ~10% is the classic footprint of bought or manipulated links.

## Backlink Audit and Disavow

When to audit:

- After any ranking drop correlated with a spam update
- When acquiring a domain/website
- On unusual backlink growth you didn't create
- Annually as maintenance

Red flags:

| Signal | Risk |
|--------|------|
| Sudden spike in links from unrelated sites | Possible negative SEO or old PBN |
| High % of links from foreign-language sites (if not multilingual) | Spam |
| Known PBN patterns (same IP, similar design, thin content) | Penalty risk |
| Anchor text dominated by exact-match commercial terms | Over-optimization |
| Links from penalized/deindexed sites | Possible contagion |

Disavow process:

1. Export link profile from GSC + Ahrefs/Semrush
2. Identify clearly toxic links (spam, PBN, paid)
3. Attempt removal by contacting webmasters (document attempts)
4. Create disavow file for remaining toxic links: UTF-8/ASCII `.txt`, one entry per line, `domain:example.com` for whole domains or a full URL for one page, `#` starts a comment (Google spec; 100K-line / 2MB cap)
5. Submit via GSC Disavow Tool
6. Monitor for impact over 2-4 months

Disavow is a scalpel for clearly toxic links, not a routine tool — disavowing merely mediocre links removes whatever value they had.

## Brand Signals and Unlinked Mentions

Brand mentions without links are valued as trust signals. Working the channel:

1. Monitor brand mentions (Google Alerts, Mention.com, Ahrefs)
2. Contact authors to request a link when mentioned without one
3. Respond to mentions to build relationships for future linked coverage

Top AI source sites (ChatGPT citation analysis): Wikipedia (highest), Forbes (very high), NerdWallet, Bankrate, TechRadar, Tom's Guide, CNBC (all high). Pattern: authoritative, well-known brands with strong entity recognition get cited most by AI systems.

### Brand-SERP audit (cheapest high-trust win)

The SERP for your own brand name is the one results page you largely control, and nearly every
serious prospect checks it. Quarterly: search the brand, plus brand + "review" / "pricing" /
"alternative", and verify: homepage at #1 with sensible sitelinks; Knowledge Panel claimed and
accurate; owned profiles (LinkedIn, YouTube, GBP) filling page 1; no stale or negative surprise
outranking owned pages. Fixes are ordinary tactics already in this file: entity signals, profile
completeness, and an honest page on your own site for each high-intent brand query ("[brand]
pricing", "[brand] vs X") before a third party answers it for you.

## Entity SEO — Knowledge Graph End-to-End

Entity SEO = optimizing for Google's understanding of things (people, brands, places, concepts) and their relationships, not keywords. In 2026 this is the primary mechanism for AI search visibility.

Why it matters — all four rows below are Apr 2026 internal-benchmark figures, none re-confirmed mid-2026;
the mechanism (not these magnitudes) is what the Ahrefs correlations corroborate:

| Metric | Value |
|--------|-------|
| Sites optimizing for entities vs keyword-only | 40% more AI-generated citations |
| Brands with verified Knowledge Graph entities | 3.1x more AI citations |
| Brands actively managing entity data that have Knowledge Panels | 72% |
| Brands NOT managing entity data that have Knowledge Panels | 14% |

The load-bearing 2026 evidence for the mechanism is the Ahrefs 75K-brand correlation study (branded mentions/search volume as top AI-visibility factors) — cite that instead of the two legacy magnitudes above; see `ai-search-geo.md` §4 and its superseded-claims ledger.

Knowledge Graph = Google's entity/relationship database (the brain). Knowledge Panel = the SERP card (the screen). An entity can exist in the Graph without triggering a Panel; panels appear once Google is confident the entity is well-defined.

### Three pillars

1. **Precision** — every page unambiguously about one canonical entity: title tag, H1, `mainEntityOfPage`, URL slug, and body all reference the same entity.
2. **Coverage** — the site collectively represents the entities and sub-topics defining its niche (a mini Knowledge Graph): topic clusters per entity, all attributes covered, sub-entities addressed, relationships mapped.
3. **Connectivity** — internal links connect related entities; `sameAs` schema links verified external profiles; schema relationship chains (`Product -> Category -> Brand`); related entities mentioned naturally in content.

### Building a branded entity — essential signals

| Signal | Where | Priority |
|--------|-------|----------|
| Wikidata entry | wikidata.org | Critical — structured data Google directly uses |
| Wikipedia page | wikipedia.org | Highest authority (only if genuinely notable) |
| Google Business Profile | Google | Critical for physical-presence businesses |
| Organization schema with `sameAs` to all profiles | Your site | Critical |
| Consistent NAP | Across all platforms | High |
| Social profiles (LinkedIn, X, Crunchbase) | Referenced via `sameAs` | High |
| Press coverage | News sites | High — independent mentions build confidence |
| Industry directories | Relevant directories | Medium — corroborating sources |
| Author entity (Person schema, `knowsAbout`, profile `sameAs`) | Your site + profiles | Medium — E-E-A-T |

Entity confidence score (what AI systems weigh): (1) number of independent sources describing the entity consistently, (2) authority of those sources (Wikipedia > random blog), (3) presence of structured data explicitly declaring entity attributes. The `sameAs` array is the corroboration wire: it must point at profiles that actually exist and agree with each other.

Organization schema shape: `@type: Organization` with `@id`, `name`, `url`, `logo`, `foundingDate`, `founder` (Person with own `sameAs`), `sameAs` [Wikidata, Wikipedia, LinkedIn, X, Crunchbase], `contactPoint`, `address`. Author entity: `@type: Person` with `@id`, `jobTitle`, `worksFor`, `sameAs` [LinkedIn, X, GitHub], `knowsAbout` array.

### Knowledge Panel playbook

If a panel exists: search brand name → "Claim this knowledge panel" → verify via associated accounts → suggest edits (Google reviews and applies).

If no panel exists, build signals until Google is confident:

| Action | Timeline |
|--------|----------|
| Create/claim Wikidata entry | Week 1 |
| Organization schema on website | Week 1 |
| Claim GBP (if applicable) | Week 1 |
| Complete social profiles, consistent info | Week 2 |
| Earn press mentions from authoritative sources | Ongoing |
| Wikipedia page | Only when notability criteria met |
| Monitor via brand search queries | Ongoing |

### Optimizing for AI entity recognition

| Do | Why |
|----|-----|
| Use entity names consistently | Don't switch between "JS", "JavaScript", "ECMAScript" randomly |
| Define entities on first mention | "Next.js, a React framework by Vercel, enables..." |
| Link to entity sources | Wikipedia, official docs, authoritative references |
| Use structured data | Machine-readable entity declarations |
| Build entity co-occurrence | Mention related entities together naturally |
| Cross-platform consistency | Same entity info everywhere |

AI systems and their entity sources: Google AI Overviews (Knowledge Graph + Gemini, pre-filters trusted entities), ChatGPT (training data + Bing, favors Wikipedia/Forbes-grade sources), Perplexity (real-time crawling, cites strong web presence), Claude (training data + search, relies on entity clarity).

### Topical maps and clustering

1. Identify the core entity (what the site is fundamentally about)
2. Map sub-entities (related concepts, attributes, use cases)
3. Identify relationships between sub-entities and core
4. Map each entity/sub-entity to a content piece
5. Build internal links that mirror the entity relationships

Intent-first clustering (2026): group by search intent and journey stage, not word similarity; 15-30 keywords per cluster (optimal balance, vs 100+ lexical grouping); review clusters quarterly against SERP changes. SERP-based clustering: if two keywords share 3+ ranking URLs, they belong in the same cluster.

## Competitor Gap Analysis — Five-Gap Framework

| Gap type | What to analyze | Tools |
|----------|----------------|-------|
| Keyword gap | Keywords competitors rank for that you don't | Semrush, Ahrefs |
| Content gap | Topics competitors cover with greater depth/breadth | Semrush Content Gap, manual audit |
| Backlink gap | Referring domains linking to competitors but not you | Ahrefs Backlink Gap, Semrush |
| Technical gap | CWV, crawlability, indexation, schema | PageSpeed Insights, Screaming Frog |
| SERP feature gap | Rich results competitors own (snippets, PAA, panels) | SERP tracking tools |

Keyword gap process: intersect your domain with 3-5 SERP competitors → filter for competitor positions 4-20 (leapfrog opportunity) → filter KD below your authority threshold → group by intent → map to content plan → prioritize by volume x conversion potential.

Backlink gap process: compare referring domains across 3-5 competitors → shortlist sites linking to 2+ competitors but not you → classify link type (editorial, resource page, guest post) → assess outreach viability → prioritize by authority and topical relevance → run targeted outreach per opportunity type.

Cadence: monthly ranking-change review; quarterly full keyword + backlink gap refresh; after every core update, impact comparison across the competitor set; annual strategy reset.

## Reddit and Community Presence

Reddit's standing (internal-benchmark figures): #2 Google visibility (after Wikipedia); 108M daily actives; 1B monthly visits; present in 97% of search queries; $60M/year Google licensing deal for content/AI training. Google's August 2024 "hidden gems" update prioritized authentic community content; engagement signals (upvotes, comments) act as quality proxies.

| Do | Don't |
|----|-------|
| Answer-first, genuinely helpful posts | Promotional links without genuine value |
| Write like a real user, not a marketer | Fake accounts / astroturfing |
| Cover multiple angles, cite data + experience | Copy-paste the same answer across subreddits |
| Consistent contribution history in relevant subreddits | Carpet-bombing; ignoring subreddit rules (ban) |
| Personal accounts with history | Brand accounts exclusively (personal performs better) |

## Programmatic SEO — Legitimate vs Doorway Territory

| Good fit | Bad fit (doorway territory) |
|----------|---------------------------|
| Location pages ("[service] in [city]") with real local data | Single-product businesses |
| Comparison/alternatives pages | Topics requiring deep expertise |
| Tool/calculator pages with varying inputs | YMYL content without professional oversight |
| Data-driven pages (statistics, pricing databases) | Thin content adding no unique value |
| Integration pages ("[product] + [integration]") | AI-generated content shipped without review |

**The uniqueness test:** remove the variable (city name, product name) from the page. If the remaining content isn't still useful, the template is too thin — that is doorway-page territory.

Mandatory quality gates: Batch 1 = 20-50 pages (validate template quality, engagement, indexing) → Batch 2 = 100-300 (build hubs/clusters, monitor impressions/clicks) → Batch 3 = 1,000+ only after clusters show real engagement signals.

Template requirements: dynamic content (images, FAQs, CTAs, reviews vary per page), conditional sections by data attributes, local/contextual data specific to the variable, automated internal links within the cluster, dynamic schema, unique meta tags.

Risk mitigation: Scaled Content Abuse policy → genuine per-page value + human review of samples; thin-content classification → minimum 300 words of unique useful content per page; index bloat → monitor GSC coverage, noindex underperformers; crawl budget → sitemap only high-value pages; negative user signals → A/B test the template before scaling.

Expected results when done right (internal-benchmark figures): 200-500% organic traffic increase within 6 months; keyword coverage from ~50 to 10,000+ variations; 30-50% higher conversion vs broad blog posts (long-tail intent).

## SaaS/B2B Specifics

Full-funnel content map:

| Stage | Content | Keywords |
|-------|---------|----------|
| TOFU | Blog posts, thought leadership, original research | "what is [concept]", "how to [task]" |
| MOFU | Comparison pages, alternatives pages, case studies | "[product] vs [competitor]", "[product] alternatives" |
| BOFU | Feature, pricing, integration pages, demos | "[product] pricing", "buy [product]" |
| Post-purchase | Help docs, tutorials, community | "[product] how to [task]" |

Comparison pages are the highest-conversion SaaS content (users narrowed to 2-3 options): compare fairly (acknowledge competitor strengths), side-by-side feature table, "Choose X if..., choose us if..." guidance, switcher testimonials, Product schema with ratings for both, target "[You] vs [Competitor]" and "[Competitor] alternative".

Product-led SEO — pages that are both SEO targets and product discovery: `/features/*`, `/integrations/*`, `/templates/*`, free `/tools/*` (calculators), `/solutions/*` use-case pages.

2026 B2B shifts (internal-benchmark figures): 94% of B2B buyers use LLMs during the purchase journey → optimize for AI citation via entity SEO + structured content; educational blog value declining (AI answers basics) → differentiate with original research; zero-click hitting B2B queries → invest in brand building + bottom-funnel conversion content; founder-led LinkedIn content builds pre-website trust and branded search volume.
