# Usage guide — seo-optimization

How to use the skill day to day: what triggers it, what each workflow does, three worked
walkthroughs, and troubleshooting. Install instructions are in [README.md](README.md); the full
doctrine lives in [`skills/seo-optimization/SKILL.md`](skills/seo-optimization/SKILL.md).

## How it triggers

The skill loads automatically when a request looks like SEO work: rankings, organic traffic,
keyword research, titles/meta/headings, structured data, internal linking, Core Web Vitals for
search, E-E-A-T, backlinks, AI-search visibility (AI Overviews, AI Mode, ChatGPT, Perplexity),
traffic drops, indexing problems, penalties, migrations, new-site setup, local/GBP, e-commerce,
YMYL, video/image, or international SEO. To force it, invoke the Skill tool with
`seo-optimization` (plugin installs: `seo-optimization:seo-optimization`).

It also triggers on the *temptation* cases — "should we add keywords/schema/SEO copy here?" —
because deciding what NOT to add is half the skill.

## What to expect once it loads

Every engagement follows the same spine:

1. **Intent validation first.** The live SERP for the target queries gets checked before
   anything is written: page type, format, who ranks, features present. Content type must match
   the SERP pattern, and the destination test runs (is this site the natural endpoint for the
   query, or a layer in between?). If live data isn't reachable, assumptions get labeled as
   assumptions rather than asserted.
2. **A policy/risk preflight** on anything smelling of scale: "maximum pages", "GEO hacks",
   programmatic variants, expired domains. Requests that classify as scaled content, doorway
   pages, or AI-response manipulation get declined with the compliant alternative, not silently
   executed.
3. **Audit before optimizing** on existing sites — three read-only lenses (SERP/competitor,
   in-repo technical with file:line evidence, deployed crawlability via rendered Googlebot-UA
   fetches). GSC-sourced findings are classified LIVE-DEFECT / ALREADY-FIXED / INTENDED before
   any fix ships, because GSC describes Google's last crawl, not your current deploy.
4. **Implementation through the naturalness gate** — would this element read the same if search
   engines didn't exist? Keyword-container titles, query-mapped headings, entity stuffing, and
   boilerplate keyword edits all fail the gate regardless of which "signal" justifies them.
5. **Verification before "done"**: rendered production capture with a Googlebot UA, Rich
   Results Test on changed schema, sitemap entries shipped in the same change, a red-flags
   self-check on the final diff.
6. **Honest diagnosis**: most "why aren't we page 1" cases are majority off-site authority.
   The skill states the split and realistic timelines instead of selling on-page busywork —
   and then works the winnable non-branded middle anyway.

## Walkthrough 1: auditing a deployed site

**Ask:** "Why isn't our /guides section ranking? Audit the site's SEO."

The skill checks the live SERP for the section's target queries first (a format mismatch is the
P0 finding, not a technical tweak), then runs the three audit lenses and merges them into a
P0→P3 prioritized fix list where every item carries file:line or rendered-HTML evidence. Where
the repo and the deployed capture disagree, the deployed capture wins — that's a build/deploy
gap to investigate, not an average. The diagnosis ends with the honest on-site/off-site split
and timelines, never a promise that title tweaks will win head terms.

## Walkthrough 2: ranking for what the site does (non-branded)

**Ask:** "We rank #1 for our name and nowhere for anything we actually do."

The skill applies `reference/keyword-strategy.md`: enumerate the site's functions (every task,
dataset, tool, or lookup a user can complete), derive the query set per function in the four
phrasings users actually type (task, object, problem, comparison), validate against GSC
striking-distance data (positions 4-20), autocomplete/PAA, internal site-search logs, and the
competitor keyword gap. The output artifact is the query→page map — every target cluster owned
by exactly one page, no new URL without a map row — worked bottom-up along the
authority-relative ladder: striking distance → KD 0-29 function long-tail → cluster middles →
head terms last. Success is measured on the non-branded scoreboard, reported separately from
branded traffic. Nobody is told to "wait a year for brand authority": authority sets the
ceiling; coverage fills everything under it, in parallel.

## Walkthrough 3: traffic-drop triage

**Ask:** "Organic clicks fell 25% this month, and GSC shows a pile of indexing errors."

The seven-step runbook in `reference/measurement-and-audit.md` runs in order, cheapest decisive
checks first: (1) is the drop real (GSC vs analytics divergence = tracking breakage), (2)
manual actions/security, (3) update timing vs the Search Status Dashboard (no panic edits
mid-rollout), (4) technical regressions from recent deploys verified against live
Googlebot-UA fetches, (5) SERP-shape shifts (AI Overviews arriving on your money queries), (6)
year-over-year seasonality, (7) competitive erosion/decay. Every comparison is segmented three
ways — by template, branded vs non-branded, and search type — before any conclusion. GSC bucket
findings get the lag discipline: only defects that reproduce live today become engineering
tickets; the rest are re-crawl requests or intended behavior.

## Everyday small asks

The skill is not only for big engagements:

| Ask | What happens |
|---|---|
| "Write the title and meta for this page" | One natural primary phrase + a true differentiator, 50-60 chars, brand last; meta as a one-sentence pitch. Keyword containers refused with the reason |
| "Should this page have schema?" | Only types the page visibly IS, with real data; retired rich-result types (FAQ, HowTo) flagged instead of cargo-culted |
| "Our CTR is bad at position 4" | The monthly CTR quick-win loop: GSC filter, title rewrite through the gate, annotate, re-measure at 28 days |
| "Check our robots.txt / sitemap" | Coordination check across robots/sitemap/canonicals as one unit, plus a sitemap sample-probe (random URLs must be 200, self-canonical, no noindex) |
| "How do we appear in AI answers?" | The evidence-graded GEO playbook: indexable + snippet-eligible, answer-first passages, brand mentions and comparative content — and a clear no on llms.txt and schema-as-AI-hack |

## Troubleshooting

| Symptom | Cause | Fix |
|---|---|---|
| Skill doesn't trigger on an SEO-shaped prompt | Not installed, or the prompt misses the trigger description | `claude plugin list` to verify install; invoke the Skill tool directly by name |
| Recommendation reads keyword-stuffed even though no single element looks spammy | Systematic mild over-optimization — the exact failure the skill gates | Re-run the naturalness gate and red-flags self-check in SKILL.md against the element |
| A schema change breaks rich results | Markup diverges from visible content, or an eligibility-only field lacks real data | `reference/structured-data.md` mirror-visible-content rule; validate with the Rich Results Test; never fabricate `aggregateRating` |
| GSC reports problems the live site doesn't show | GSC reflects Google's last crawl — days to weeks stale | Apply the lag discipline: classify LIVE-DEFECT / ALREADY-FIXED / INTENDED via a live Googlebot-UA fetch before filing fixes |
| Deliverable promises rankings from on-page tweaks alone | The honesty rule was skipped | Re-read SKILL.md's honesty rule: state the on-site/off-site split and 6-24-month algorithmic timelines |
| Plugin update installed but a running session behaves old | Live sessions cache loaded plugins | `/reload-plugins`, or start a new session |

## Updating

Plugin installs: `claude plugin update seo-optimization@seo-optimization`. Symlink installs:
`git pull` in the clone. Release notes accompany every version on the
[Releases page](https://github.com/TheMizeGuy/seo-optimization-public/releases).
