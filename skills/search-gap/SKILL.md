# Search Gap Analysis

A search discoverability and competitive gap analysis tool that audits a website's on-page SEO health, E-E-A-T trust signals, and content depth against 21 checks drawn from Google's official documentation, industry-standard SEO research, and content marketing studies. Then identifies semantic competitors from live SERP data and recommends content pillars scored on relevance, difficulty, and volume.

## Purpose

Analyze a website's full content footprint — homepage, product pages, and all blog posts — to identify search discoverability gaps, competitive blind spots, and strategic content opportunities. The output is a three-section report: on-page audit (21 checks), competitive landscape (SERP-based), and content pillar recommendations (scored on a Goldilocks balance).

## How It Works

1. **Discover & crawl** — WebFetch the homepage, find the blog/resources section, crawl ALL blog posts and key product pages
2. **Audit 21 checks** — evaluate every check across the crawled pages as PASS/FAIL/N/A
3. **Map the competitive landscape** — extract 5 core topics, WebSearch each, identify top 3 SERP competitors, analyze their content advantages and gaps
4. **Recommend content pillars** — synthesize audit gaps + competitive gaps into 3-5 scored content opportunities

## The 21-Check Playbook

### 1. Technical SEO (8 checks: TS-1 to TS-8)
Schema.org structured data, meta title optimization, meta description quality, heading hierarchy, internal linking structure, image optimization, canonical tags & URL structure, Open Graph & Twitter Card metadata.
> See [reference/technical-seo.md](reference/technical-seo.md)

### 2. E-E-A-T Signals (7 checks: EA-1 to EA-7)
Author attribution, About page depth, original research & proprietary data, external citations, trust signals (privacy/terms/contact), case studies & customer proof, content freshness.
> See [reference/eeat-signals.md](reference/eeat-signals.md)

### 3. Content Depth (6 checks: CD-1 to CD-6)
Content depth per page, topic coverage breadth, FAQ & educational content, visual content quality, content architecture (pillar/cluster), funnel content balance (TOFU/MOFU/BOFU).
> See [reference/content-depth.md](reference/content-depth.md)

## Scoring

Each section receives a letter grade (A+ through F) based on the percentage of applicable items that pass:

| Grade | Pass Rate |
|-------|-----------|
| A+    | 100%      |
| A     | 90-99%    |
| A-    | 85-89%    |
| B+    | 80-84%    |
| B     | 75-79%    |
| B-    | 70-74%    |
| C+    | 65-69%    |
| C     | 60-64%    |
| C-    | 55-59%    |
| D+    | 50-54%    |
| D     | 45-49%    |
| D-    | 40-44%    |
| F     | Below 40% |

Items marked N/A are excluded from the denominator.

## Output Format

### Section 1: On-Page Audit
For each of the 21 checks, the report includes:
- **What it is** — description of the check (from the reference)
- **Why it matters** — the rationale (from the reference)
- **Source** — full citation
- **Compliance** — PASS, FAIL, or N/A
- **Observation** — what was specifically observed across the crawled pages
- **How to fix** — concrete, actionable recommendation (only if FAIL)

### Section 2: Competitive Landscape
For each of the top 3 semantic competitors:
- Domain & SERP presence (appeared in X/5 topic searches)
- Content advantage (what they do better)
- Content gap (what they're missing — the client's opportunity)
- E-E-A-T comparison

### Section 3: Content Pillar Recommendations
For each of 3-5 recommended pillars:
- Pillar title and description
- Relevance / Difficulty / Volume scores (High/Med/Low)
- Opportunity score (Goldilocks formula)
- 3-5 specific article topics with target intent and format

## Sources

Checks are drawn from:
- Google Search Central documentation and Google Developers guidelines
- Google Search Quality Rater Guidelines (December 2024)
- web.dev performance and accessibility guidelines
- Moz SEO Learning Center and research
- Ahrefs research and case studies
- Backlinko content and ranking factor studies
- SEMrush SERP and content analysis research
- HubSpot content marketing research
- Content Marketing Institute benchmarks
- Open Graph Protocol specification
