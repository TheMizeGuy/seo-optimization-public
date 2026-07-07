# AI Search & GEO — Current State (July 2026)

Purpose: what an agent doing SEO work on any site must know about AI Overviews, AI Mode, and AI assistants as of July 2026 — current numbers, Google's official doctrine, what earns citations, crawler/robots strategy, and measurement.

## 1. Headline correction — read first

| Claim circulating widely | Reality (primary-sourced) |
|---|---|
| "AI Mode became Google's default search experience at I/O 2026" | **Overstated — false as of July 2026.** Google's own I/O 2026 post (blog.google, May 19-20, 2026) says **Gemini 3.5 Flash became the default model WITHIN AI Mode** globally (~200 countries, 98 languages); it does not say AI Mode replaced the classic SERP. Lumar's May 2026 roundup explicitly confirms AI Mode was NOT made the default. AI Mode was only **~0.34% of search sessions** Jan-Apr 2026 (Seer Interactive, 25.1M impressions). Google did report AI Mode passed **1B monthly users** with queries doubling quarterly — big and growing, but not "the default SERP" |

Operative posture: AI Overviews are the at-scale CTR suppressor today; AI Mode is a near-total click black hole (93% zero-click, Seer 2026) that is still a small share of sessions. Monitor its growth post-I/O; do not panic-report historical damage or build plans on "AI Mode is the default."

## 2. AI Overviews / AI Mode — current state

### Trigger rates (tracker-dependent; supersedes the old "~58% trigger rate")

| Period | AIO coverage | Tracker / source |
|---|---|---|
| Jan 2025 | 6.49% | Semrush, 10M+ keywords (via Omnibound 2026) |
| Jul 2025 (peak) | 24.61% | Semrush |
| Q1 2026 | 25.11% | Conductor, 21.9M queries |
| Feb 2026 | ~48% | BrightEdge Generative Parser |
| Feb 2026 | "roughly 50% of US queries" | Google official statement |

Honest 2026 range: **~25% (Semrush/Conductor, commercial-skewed keyword sets) to ~50% (BrightEdge / Google, US)**. The "~58% trigger rate" (Apr 2026 internal baseline) matches no mid-2026 tracker — superseded.

By industry (BrightEdge, Feb 2026): healthcare 88%, education 83%, B2B tech 82%, restaurants 78%, **e-commerce collapsed to ~4%** (from 29%) — Google pulled AIOs off transactional queries and monetizes them with Shopping units instead.

### CTR impact — severe, but with a measured rebound

| Finding | Number | Source (date) |
|---|---|---|
| Organic CTR on AIO queries bottomed, then rebounded | ~1.3% Dec 2025 → 2.4% Feb 2026 (+85% in 2 months; earlier Seer editions reported a 0.61% floor Sep 2025 — quote the study edition) | Seer Interactive update, Apr 24, 2026 (53 brands, 5.47M queries, 2.43B impressions) |
| Structural gap, AIO vs no-AIO queries | 2.4% vs 3.8% CTR = **~37% gap is the new baseline**, not the 2025 free-fall | Seer (Feb 2026 data) |
| Cited in the AIO vs not cited | **+120% more organic clicks per impression** (still ~38% below no-AIO scenarios) | Seer 2026 |
| Position-1 CTR when AIO present | −34.5% to −58% | Ahrefs, 300K keywords (Dec 2025) |
| Field experiment on triggered queries | −38% outbound organic clicks; zero-click 54% → 72%; forced-AI-Mode users clicked less AND were less satisfied | 2026 field study via SEJ [single-source, directionally consistent with Pew 2025] |
| 12-month decoupling | Impressions +49%, click-throughs −30% | BrightEdge |
| Zero-click share, all Google searches | ~64.8-68% (2026) — supersedes "60% (Semrush 2025)" | SparkToro 2026 study |
| Paid CTR with AIOs present | Rose 14.6% → 16.2% | Seer 2026 |
| Aggregate organic growth | 26.3%/yr pre-AI-search → 3.7%/yr after | Tank Google AI Search Shift Report [single-source] [vendor] |

Nuance to keep: Semrush 10M-keyword study (late 2025/early 2026) — zero-click rate on keywords *after* gaining an AIO fell slightly (33.75% → 31.53%). AIO-triggering keywords are informational and already high-zero-click; the AIO is not the sole click thief.

Strategy consequence: the winning posture is **"get cited"** (chase the +120% citation premium), not "mourn clicks."

### AI Mode traffic behavior

| Fact | Number | Source (date) |
|---|---|---|
| AI Mode queries with zero outbound clicks | 93% | Seer Interactive, Jan-Apr 2026, 25.1M impressions |
| Share of searches transitioning into AI Mode (pre-I/O) | 0.34% | Seer, Jan-Apr 2026 — re-measure post-I/O |
| Of clicks that do occur in 2026 search | ~66% open web, ~27% Google properties, ~6% ads | Seer 2026 |
| AI Mode vs AIO citing the same URLs | Only **13.7%** (despite 86% semantic answer similarity); Victorious found 30-35% | Ahrefs, 730K response pairs (2026); Victorious (2026) |

AI Mode and AI Overviews are **two distinct citation systems** — track and optimize them separately.

### Ads context (why Google won't reverse course)

- Google Marketing Live 2026 (May 20, 2026): Conversational Discovery ads, Highlighted Answers inside AI Mode, AI-powered Shopping ads, Business Agent for Leads (blog.google GML post).
- Ads alongside AIOs: ~3% of SERPs (Jan 2025) → ~40% (Nov 2025) per Semrush.
- Google Search revenue Q4 2025: $63.07B, +17% YoY (Alphabet SEC filing). Web traffic falls while Google revenue rises.

## 3. Google's official doctrine — "GEO is still SEO" (May 15, 2026)

"Optimizing your website for generative AI features on Google Search" — Google's **first official AI-search optimization guide** (developers.google.com/search/docs/fundamentals/ai-optimization-guide, May 15, 2026; llms.txt subsection added June 15, 2026). This is the citable anchor for the whole topic.

| Google's position | Detail |
|---|---|
| **"Still SEO"** | AEO/GEO is not a separate optimization layer; generative AI features are rooted in core ranking/quality systems. Google explicitly tells owners to scrutinize third-party "AEO/GEO" services against standard SEO guidance |
| Eligibility for AI features | Indexed + snippet-eligible + normal technical requirements. Nothing extra |
| Explicitly NOT needed | llms.txt / AI text files / special markup or Markdown; **content chunking** ("systems can understand multi-topic pages"); AI-specific rewriting; long-tail synonym-variant rewriting; manufactured brand mentions |
| Structured data | **Not required** for generative AI features (still useful for rich results and entity disambiguation) |
| What moves the needle | Unique, valuable, "non-commodity" content with distinctive perspective; good page experience; Merchant Center / Business Profile for commerce/local |
| Agentic experiences | Optional extra-time track for businesses where agents may compare, book, buy, or inspect inventory. Prepare normal accessible web apps: crawlable public data, stable DOM, accurate product/service details, accessible names, visible availability/pricing, and secure transaction flows. Do not treat agent readiness as an SEO/GEO hack |

Companion doctrine in the same window:

- **June 5, 2026** — new "third-party SEO tools, services, and advice" doc + revised "Do you need an SEO?" guide: Google does not evaluate or endorse SEO tools; nothing is "Google-approved"; tools have no internal ranking data (developers.google.com/search/docs/fundamentals/third-party-seo).
- **May 7, 2026** — FAQ rich results fully dead (SERP feature removed entirely; GSC reporting removed June 2026, API removal Aug 2026). Keep FAQPage markup only where it aids comprehension; delete FAQ rich-result tactics from any playbook.
- Nick Fox (Google, I/O 2026 window): content that wins in AI surfaces "goes one level deeper... and is really helpful."

## 4. What earns AI citations (evidence-backed, post-March-2026)

### Brand signals >> backlinks

Ahrefs 75,000-brand correlation study (ahrefs.com, Dec 12, 2025; Spearman correlations across ChatGPT, AI Mode, AI Overviews):

| Factor | Correlation with AI visibility |
|---|---|
| YouTube mentions | ~0.737 (strongest single factor, all three platforms) |
| Branded web mentions | 0.656-0.709 |
| Branded anchors | 0.511-0.628 |
| Branded search volume | 0.352-0.466 |
| Backlinks | "Very weak correlations" |
| Content volume | ~0.194 ("almost no relationship") |

Platform texture: AI Mode is most driven by traditional brand authority; ChatGPT is least dependent on established authority (easiest entry point for smaller brands); AIOs weight domain rating slightly more (0.326). Off-site brand building and video are first-class AI-visibility levers.

### Citations ≠ brand mentions ("ghost citations")

Semrush Ghost Citations study (semrush.com, June 9, 2026; 3,981 domain appearances, 115 prompts, 14 countries, 4 platforms; term coined by Kevin Indig):

| Finding | Number |
|---|---|
| ChatGPT: cites sources / names the brand | 87% cite rate, only **20.7%** brand-mention rate — content feeds answers anonymously |
| Gemini (inverse pattern) | 83.7% mention rate, 21.4% citation rate |
| AI Mode mention rate | ~42% |
| **Comparative content** brand-mention rate | **43.3% — 2.4x informational (18%)**; how-to 42.8%; commercial 35.6% |
| Informational content | Cited 89.3% of the time but rarely named |

Practical: for brand visibility (not just link-outs), invest in comparison/evaluation/recommendation content and put the brand name inside the extractable passages.

### Freshness (quantified, converging evidence)

| Finding | Source (date) |
|---|---|
| AI-cited content is 25.7% fresher than content cited in traditional organic | Ahrefs, 17M citations |
| 65% of AI bot hits target content published within the past year; 89% within three years | Seer Interactive, 5,000+ URLs |
| AIOs most recency-biased (44% of citations from 2025-dated content); ChatGPT keeps a long tail (still cites 2004 pages); Perplexity reacts to updates within days | Am I Cited + aggregations (2026) |
| ~Half of AI-cited content is <13 weeks old; <30-day content earns ~3.2x more citations | ConvertMate, 80M citations [vendor, directionally consistent with Ahrefs/Seer] |

Real updates and honest datelines — not date-bumping.

### Structure and position

| Finding | Source (date) |
|---|---|
| 44.2% of AIO citations come from the first 30% of a page's content — answer-first ordering matters. Compatible with Google's "no chunking needed": put the answer early, don't fragment pages | SparkToro, Jan 2026 (via Omnibound) |
| Citation concentration: YouTube 23.3% + Wikipedia 18.4% of AIO citations; Reddit ~21%; top 15 domains = 68% of 680M citations | Surfer SEO (46M citations); DemandSage; 5WPR Citation Index |
| Counterweight: brand-owned sites rose to 31% of citations, up from 26% — owned content is gaining citation share | Presenc AI, 84K queries, Apr 2026 |

### The overlap collapse (major post-2025 delta)

AIO-citation overlap with top-10 organic fell from **~76% (mid-2024) to 17-38% (Feb 2026)** (BrightEdge vs. ALM Corp divergence). 62-83% of AIO citations now come from pages OUTSIDE the top 10. Ranking #1 no longer implies citation, and citation no longer requires top-10. Citation is a partially separate game won by: extractable answer-first passages, comparative content, brand name in the passage, freshness.

### The destination pattern (core-update evidence — the winning posture)

Two consecutive 2026 core updates (March 27-Apr 8; May 21-Jun 2) moved visibility from **intermediaries** (aggregators, comparison hubs, commentary/summary layers, OTAs, social/UGC surfaces — YouTube, Reddit, TripAdvisor, Expedia among the losers) to **first-party destinations** (official institutions, direct brands, specialist publishers, canonical references). May-core winner drivers: intent match, market fit, source type (Sistrix 8,887-domain dataset; Aleyda Solis / SEJ analyses, Jun 2026).

Apply a **destination test** to every content plan: is this site the natural endpoint for the query (owns the data / inventory / expertise), or a layer between the user and the answer? Being the first-party destination is the winning pattern for classic ranking AND AI citation. Aggregation-shaped content is structurally at risk regardless of polish.

## 5. Evidence-backed practice vs. vendor hype

Evidence-backed (2+ independent sources):

1. Be indexable + snippet-eligible — the hard prerequisite for every engine (Google, OpenAI, all retrieve from search indexes).
2. Build brand mentions across the web + YouTube presence (Ahrefs correlations; strongest known lever).
3. Answer-first structure: extractable, self-contained answer passage early in the page (SparkToro position data; Seer citation click premium).
4. Comparative/evaluative content for brand mentions; informational content accepts ghost-citation economics (Semrush).
5. Keep priority pages genuinely fresh (Ahrefs / Seer / platform data).
6. Track per engine — ChatGPT, Gemini, AIO, AI Mode behave measurably differently (Semrush; Ahrefs 13.7% overlap).

Vendor hype / unverified — do NOT state as fact:

| Claim | Status |
|---|---|
| "74.2% of AI citations come from Top-N listicles", "triple JSON-LD schema stacking", "7-14 day freshness cycles", "publish 1-2 listicles weekly" | Single GEO-tool vendor (GenOptima) [single-source] [vendor]; contradicted by Google's "no special format" guidance |
| "+41% from quotations, +32% from statistics, +30% from citations" | The 2023 Princeton GEO paper, measured on a research testbed — directional evidence for extractability at best; misleading when sold as fresh 2026 platform data |
| Schema markup as an AI-citation ranking factor | Google explicitly says structured data is not required for AI features; no credible 2026 study shows causal schema→citation lift. Keep schema for disambiguation and rich results only |
| "Entity-optimized content = +40% AI citations" | Legacy claim (Apr 2026 internal benchmark) not re-confirmed by any mid-2026 primary study — treat as unverified |
| "Author entity verification" / "Author Vectors" mechanics; "+22% original data / −71% AI-paraphrased" | Not Google-confirmed; practitioner inference [single-source class — unverified] |

## 6. llms.txt — verdict: dead as an SEO/GEO lever

| Party | Position (date) |
|---|---|
| Google | Formally ignores it — the official AI-optimization guide's llms.txt subsection (June 15, 2026) says Google Search including all generative AI features ignores llms.txt ("will neither harm nor help"). Earlier: Gary Illyes (Jul 2025) no support planned; John Mueller compared it to the keywords meta tag |
| OpenAI | No support; crawler docs govern everything through robots.txt, never mention llms.txt |
| Anthropic / Perplexity | Publish llms.txt for their OWN docs sites; neither confirms their assistants read other sites' llms.txt at inference |
| Adoption data | SE Ranking, 300K domains: 10.13% adoption, **no measurable effect on AI citation likelihood** (model performed slightly better without it as a feature) |

Verdict: zero evidence of citation benefit; explicit non-support from Google; no inference-time commitment from anyone. The one real (narrow) use case: developer-documentation sites consumed by coding agents / RAG pipelines / MCP integrations. Implement only there; never sell it as an AI-visibility tactic.

## 7. AI crawler landscape and robots strategy (mid-2026)

### Crawler map — three-tier pattern (training / search-retrieval / user-triggered); each token needs its own robots.txt directive

| Operator | Training | Search/retrieval | User-triggered | Trap to know |
|---|---|---|---|---|
| OpenAI | GPTBot | OAI-SearchBot (block = out of ChatGPT search answers) | ChatGPT-User (may not honor robots.txt like a crawler) | Fully separated tokens since late 2024 |
| Anthropic | ClaudeBot | Claude-SearchBot | Claude-User | All three documented robots.txt-respecting; independent tokens |
| Google | Google-Extended (Gemini **training** opt-out ONLY) | Googlebot (feeds Search AND AIO/AI Mode) | Google-Agent — explicitly ignores robots.txt | **Blocking Google-Extended does NOT remove you from AI Overviews/AI Mode.** Use Search Console's **Search generative AI control** where available (rolling out to a subset of owners) to exclude links/content from AIO, AI Mode, and gen-AI Discover without affecting ordinary Search ranking/inclusion; otherwise snippet/index controls affect regular Search too |
| Microsoft | — | Bingbot (feeds Bing + Copilot) | Copilot Actions uses ordinary browser UAs | Blocking Bingbot = out of Copilot |
| Perplexity | — | PerplexityBot | Perplexity-User | Compliance disputed — accused by Cloudflare (2025) of stealth crawling with undeclared UAs; delisted as Verified Bot; unresolved as of mid-2026 |
| Meta | Meta-ExternalAgent | — | Meta-ExternalFetcher | |
| Amazon | Amazonbot (page-level `noarchive` opts out of training) | — | — | |
| Apple | Applebot-Extended (training opt-out token) | Applebot (Siri/Spotlight/Safari) | — | Applebot-Extended doesn't affect search inclusion |
| Common Crawl | CCBot (upstream dataset for most open-source LLMs) | — | — | Blocking removes you from most open-model training data |
| ByteDance / xAI | Bytespider / Grok | — | — | Undocumented; behavioral evidence of non-compliance / spoofed UAs |

Doctrine (No Hacks, Apr 13, 2026): "Respecting robots.txt is a vendor-level property, not a category-level one." robots.txt is an honor system; enforcement lives at the CDN/WAF layer.

### Economics — crawl-to-refer ratios (Cloudflare Radar, May-Jun 2026)

- Anthropic **~11,992 pages crawled per 1 referral** (was ~24,000:1 in Q1 2026); OpenAI ~1,057:1; Google ~5:1.
- Search-purpose crawling (the kind that can return a citation) was **under 10%** of AI crawler requests in May 2026; ~90% is training/extraction.
- Over 50% of AI crawler traffic re-fetches unchanged pages (via TechCrunch, Jul 1, 2026).
- Caveat (Cloudflare's own): native ChatGPT/Claude apps strip Referer headers, so ratios overstate the imbalance.

### Cloudflare enforcement escalation

- Baseline (Jul 2025): AI crawlers blocked **by default for new Cloudflare zones**; Pay Per Crawl (HTTP 402) closed beta.
- **Jul 1, 2026 Cloudflare policy** ([official blog](https://blog.cloudflare.com/content-independence-day-ai-options/)):
  Cloudflare now classifies AI traffic by purpose: Search, Agent, and Training. From **Sept 15, 2026**, new domains on Cloudflare will block
  Training and Agent crawlers by default on pages that display ads while Search remains allowed by
  default. Multi-purpose crawlers are enforced by all of their behaviors, so Search+Training bots
  can be blocked when the owner blocks Training. Existing customers can opt out or change settings
  before the switch.
- Pay Per Crawl → "Pay Per Use" (paid when content appears in an answer, not merely fetched). Partners: Ceramic.ai, You.com. No major AI lab (OpenAI/Anthropic/Google) has signed on as of Jul 2026.

### robots.txt strategy trade-offs

| Decision | Guidance |
|---|---|
| Search/retrieval + user-triggered bots (OAI-SearchBot, Claude-SearchBot, PerplexityBot, Bingbot, *-User) | **Allow** if you want AI citations and AI-referred visitors; blocking removes you from those answer surfaces (OpenAI documents this explicitly) |
| Training bots (GPTBot, ClaudeBot, Meta-ExternalAgent, CCBot, Google-Extended, Applebot-Extended) | Content-licensing decision with no citation-visibility cost today. CCBot caveat: blocking removes you from most open-source-model training data. "Training presence feeds long-run model memory of your brand" is industry speculation — treat as unproven |
| Ad-monetized sites (emerging mid-2026 default posture) | Allow search/user bots, block training bots, enforce at CDN (Cloudflare AI Crawl Control / audit), watch the Sept 15, 2026 default flip |
| Google | Prefer the Search Console **Search generative AI control** where available: `Include` is default; `Exclude` removes links/content from AIO, AI Mode, and gen-AI Discover, is not a normal Search ranking/inclusion signal, and does not control Gemini training (use Google-Extended for that). If the property lacks access, the fallback remains snippet/index controls, which also affect regular Search presentation |

## 8. Measuring AI-referral traffic

### GA4 — native "AI Assistant" channel (new, May 2026)

Added to the GA4 Default Channel Group — confirmed in GA4 "What's New" May 13, 2026, broadly available ~June 7, 2026. Recognized referrers auto-assigned medium `ai-assistant`, campaign `(ai-assistant)`. Documented platforms: ChatGPT, Gemini, Deepseek, Copilot, Grok.

Blind spots (all confirmed):

| Hole | Consequence |
|---|---|
| **Perplexity NOT included** | Lands in Referral — must be caught with a custom channel |
| Google's own AIO / AI Mode clicks | Bucketed as **Organic Search**, not AI — invisible to the channel |
| Forward-only classification | No historical reclassification |
| Referrer-stripped clicks from native AI apps | Land in **Direct** — estimates of 1-in-3 or more AI visits hidden (35-70% range across studies — order-of-magnitude, not precise) |

Standard mitigation: layer a custom channel group with a source regex above Referral, e.g. `chatgpt\.com|chat\.openai\.com|perplexity\.ai|claude\.ai|gemini\.google\.com|copilot\.microsoft\.com|deepseek\.com|grok\.com|meta\.ai|you\.com` (Orbit Media pattern, widely replicated).

### Google Search Console — generative-AI performance reports (new, June 2026)

Announced June 3, 2026 (Google Search Central blog): dedicated reports for **AI Overviews, AI Mode, and generative AI features in Discover**.

- **Impressions only** at launch — by page, country, device, date (hourly→monthly). No clicks, no CTR, no query data.
- Phased rollout to a subset of properties (initial cohort reported UK-based); no global date.
- Before this, AI Mode clicks/impressions were silently lumped into GSC Web totals since mid-2025 with no breakdown — these are the first AI-feature-specific data Google has ever exposed.
- Related: Search Console now has a **Search generative AI control** for a subset of site owners.
  `Exclude` prevents links/content from being visible in, linked from, or used to ground AI
  Overviews, AI Mode, and generative AI features in Discover; it is not a normal Search
  ranking/inclusion signal and does not affect Gemini training.

### Third-party AI-visibility tooling

$300M+ raised in the category mid-2025→spring 2026 (Surmado landscape): Profound ($155M raised, ~$1B valuation, enterprise leader), Peec AI (challenger), Otterly (~$29/mo entry), Semrush Enterprise AIO ($99/mo add-on), Ahrefs Brand Radar (free tier, from $129/mo). All work by prompt-sampling engines at scale — inherently probabilistic (personalization, fan-out variance). Treat outputs as trend lines, not census.

### Scale context (reporting honesty)

| Fact | Number | Source (date) |
|---|---|---|
| AI referrals as share of all web visits | ~1.08% (early 2026); end-2026 projections of 20-28% of *referral* traffic are speculative | authoritytech (2026) |
| AI sources as share of publisher pageviews | <1%, despite ChatGPT referrals +200% YoY | Chartbeat via Nieman Lab, Mar 2026 |
| ChatGPT share of gen-AI referral traffic | ~64.5%, down from ~86.7% a year earlier — fragmenting toward Gemini/Claude/Perplexity/Copilot | Goodie / The Digital Bloom, Feb 2026 |
| Conversion quality | AI-referred visitors convert several-fold better than average organic (magnitudes vary widely by study — keep the claim directional) | Multiple B2B datasets, 2026 |

## 9. Entity SEO — the AI-visibility mechanism

Why it matters: AI systems use entity confidence as a pre-filter before evaluating content — weak entity recognition means weak citation odds (Apr 2026 internal benchmark). The *mechanism* is corroborated by the Ahrefs brand-signal correlations (branded mentions/search volume as top factors); the legacy *magnitude* claims ("+40% citations for entity-optimized sites", "3.1x for verified Knowledge Graph entities") were not re-confirmed in any mid-2026 primary study — treat as unverified legacy, cite the Ahrefs numbers instead.

The three pillars (precision / coverage / connectivity), the entity-signal priority table, the
branded-entity build sequence, the entity-confidence formula, and the Knowledge Panel playbook
all live in `authority-and-offpage.md` (Entity SEO section) — that file owns entity doctrine.
This section carries only the AI-specific layer below.

### AI entity recognition tactics (content-level)

The tactic table (naming consistency, first-mention definitions, co-occurrence, cross-platform consistency) lives in `authority-and-offpage.md` § Optimizing for AI entity recognition. The two AI-specific caveats to carry into any use of it:

- Schema's role per Google's May 2026 doctrine: disambiguation and rich-results aid — **not** an AI-citation ranking factor. Do not sell schema as a GEO lever.
- "Author entity verification" / knowledge-graph-traversal mechanics circulating in 2026 SEO writing: not Google-confirmed; directionally plausible practitioner inference only.

## 10. Superseded / do-not-repeat ledger

| Old claim (Apr 2026 internal baseline unless noted) | Status as of Jul 2026 |
|---|---|
| AIO trigger rate ~58% of searches | **Superseded** — matches no mid-2026 tracker; honest range ~25% (Semrush/Conductor) to ~50% (BrightEdge / Google official, US, Feb 2026) |
| AI Mode on Gemini 2.5, 180+ countries | **Superseded** — Gemini 3.5 Flash default model within AI Mode, ~200 countries, 98 languages (I/O 2026, May 19-20, 2026) |
| "AI Mode is now the default Google search experience" (circulating claim) | **False** — see §1; Google's own post + Lumar confirm not-default |
| −46.7% organic CTR when AIO present (68K-query study, 2025) | Historical. Operative 2026 frame: CTR bottomed then rebounded 85%; ~37% structural gap; +120% citation premium (Seer, Apr 24, 2026) |
| Zero-click = 60% of searches (Semrush 2025) | **Superseded** — ~64.8-68% (SparkToro 2026) |
| "Entity-optimized content +40% AI citations"; "3.1x for verified KG entities" | Unverified legacy — not re-confirmed mid-2026; use Ahrefs 75K-brand correlations instead |
| Pillar clusters lift AI citation rate 12% → 41% | Apr 2026 internal-benchmark figure without a mid-2026 re-confirmation — directional only, do not load-bear |
| FAQ rich-result optimization; FAQ/HowTo schema for SERP features | **Dead** — FAQ rich results removed entirely (Google doc note May 7, 2026) |
| "Schema markup helps AI cite your content" (Apr 2026 internal framing) | Corrected — Google (May 15, 2026): structured data not required for AI features; keep for disambiguation/rich results only |
