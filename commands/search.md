# Command: search

Analyze a website's search discoverability, identify competitive content gaps from live SERP data, and recommend scored content pillars. Exports a three-section markdown report.

## Usage
```
/saas-grader:search <url>
```

## What It Does

### Phase 1: Discover & Crawl Pages

1. **Crawl the homepage** via WebFetch to extract text content and navigation links
2. **Identify the blog/resources section** — look for links to `/blog`, `/resources`, `/insights`, `/articles`, `/learn`, or similar content hubs in the navigation
3. **Crawl the blog index** via WebFetch. Follow pagination or archive links to discover ALL blog post URLs
4. **Crawl ALL blog posts** via WebFetch — every single post, not a sample. For sites with 50+ posts, crawl up to 50 of the most recent
5. **Crawl key product/feature pages** found in the main navigation (e.g., `/features`, `/product`, `/solutions`, `/platform`)
6. **Screenshot the homepage** using local headless Chrome (NOT the browser MCP):
   - Find Chrome: `which google-chrome-stable 2>/dev/null || which google-chrome 2>/dev/null || which chromium 2>/dev/null || ls "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" 2>/dev/null`
   - Screenshot: `"/path/to/chrome" --headless --disable-gpu --no-sandbox --screenshot="[company]-homepage.png" --window-size=1280,4000 "[url]"`
   - Read the screenshot file using the Read tool to visually inspect it
   - Delete the screenshot file after inspection

### Phase 2: On-Page SEO Audit (21 Checks)

1. **Read all 3 reference files** to get the full checklist:
   - `skills/search-gap/reference/technical-seo.md` (TS-1 to TS-8)
   - `skills/search-gap/reference/eeat-signals.md` (EA-1 to EA-7)
   - `skills/search-gap/reference/content-depth.md` (CD-1 to CD-6)
2. **Score every single check** as PASS, FAIL, or N/A based on what you observed across ALL crawled pages
3. Use the same output format as the grade command: What it is, Why it matters, Source, Compliance, Observation, How to fix

### Phase 3: Competitive Landscape

1. **Extract 5 core topics** from the site's content and positioning (e.g., if the site is a project management tool, topics might be: "project management software", "task tracking best practices", "team collaboration tools", "sprint planning guide", "project management for agencies")
2. **WebSearch each topic** — run 5 searches using queries like:
   - `[topic] software`
   - `[topic] guide`
   - `[topic] best practices`
   - `[topic] tools`
   - `[topic] how to`
3. **Track domain frequency** — record which domains appear most often in the top results across all 5 searches
4. **Identify top 3 semantic competitors** — the domains with highest SERP share of voice (most appearances across the 5 topic searches). Exclude the target site itself.
5. **WebFetch each competitor's key ranking pages** — for each competitor, fetch 1-2 of their highest-appearing pages to analyze content quality
6. **For each competitor, produce a profile card:**
   - **Domain:** The competitor's domain
   - **SERP Presence:** Appeared in X/5 topic searches
   - **Content Advantage:** What they do better than the target site (depth, breadth, freshness, E-E-A-T, etc.)
   - **Content Gap:** What they're missing or weak on — the target site's opportunity
   - **E-E-A-T Comparison:** How their trust signals compare (author attribution, research, case studies)

### Phase 4: Content Pillar Recommendations

1. **Synthesize gaps** from the audit (Section 1) and competitive analysis (Section 2)
2. **Propose 3-5 content pillars** — each should address a specific gap or opportunity
3. **Score each pillar on three axes** (qualitative: High / Med / Low):
   - **Relevance:** How well it maps to the company's positioning and product
   - **Difficulty:** SERP composition signal — how strong is existing competition (brand density, content quality of current rankers)
   - **Volume:** Topic breadth proxy — how many related searches, PAA questions, and search suggestions exist around this topic
4. **Calculate Opportunity Score** using the Goldilocks formula:
   - Best: High Relevance + Low Difficulty + High Volume = **Priority 1**
   - Good: High Relevance + Med Difficulty + High Volume = **Priority 2**
   - Good: High Relevance + Low Difficulty + Med Volume = **Priority 2**
   - Okay: High Relevance + High Difficulty + High Volume = **Priority 3**
   - Okay: Med Relevance + Low Difficulty + High Volume = **Priority 3**
   - Lower priority: anything else
5. **For each pillar, recommend 3-5 specific articles:**
   - Article title
   - Target search intent (informational / navigational / commercial / transactional)
   - Recommended format (how-to guide, comparison, case study, data analysis, checklist, template)
   - Classification: Quick Win (< 1 month to rank) vs Long Play (3-6 months)

## Scoring Rules

- Score each applicable item as PASS or FAIL based on the criteria in the reference files
- Mark items as N/A ONLY when they genuinely don't apply (e.g., "content freshness" for a brand-new site, "pillar/cluster" for a site with fewer than 5 posts)
- N/A items are excluded from the pass rate — they don't count against the score
- Be honest and specific — cite what you actually observed across the crawled pages
- When uncertain, lean toward FAIL with a note about what you couldn't verify
- For items marked N/A, still include them in the output but note why they don't apply
- Technical checks (TS items) should cite specific pages as evidence, not just general impressions

## Grading Scale

Calculate a letter grade for each section based on pass rate:

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

## Output

Write a markdown file to the current working directory named `[company-name-lowercase]-search-gap.md`.

The file must follow this EXACT structure:

```markdown
# Search Gap Analysis: [Company Name]

**URL:** [url]
**Date:** [date]
**Pages Crawled:** [number] (homepage, [X] blog posts, [Y] product pages)
**Overall Audit Score:** [total pass]/[total applicable] ([overall grade])

---

## Summary

| Section | Score | Grade |
|---------|-------|-------|
| Technical SEO | X/Y | [grade] |
| E-E-A-T Signals | X/Y | [grade] |
| Content Depth | X/Y | [grade] |

---

## Section 1: On-Page SEO Audit

### 1. Technical SEO ([X/Y] — [Grade])

#### TS-1: Schema.org Structured Data (JSON-LD)

**What it is:** [Copy from reference file — word for word]

**Why it matters:** [Copy from reference file — word for word]

**Source:** [Copy from reference file — word for word]

**Compliance:** PASS | FAIL | N/A

**Observation:** [What you observed across the crawled pages — be specific. Name specific pages, cite evidence, quote what you found.]

**How to fix:** [Only if FAIL. Specific, actionable recommendation.]

---

[...repeat for every TS check...]

### 2. E-E-A-T Signals ([X/Y] — [Grade])

[...every EA check...]

### 3. Content Depth ([X/Y] — [Grade])

[...every CD check...]

---

## Section 2: Competitive Landscape

### Core Topics Searched
1. [Topic 1]
2. [Topic 2]
3. [Topic 3]
4. [Topic 4]
5. [Topic 5]

### Competitor 1: [Domain]

**SERP Presence:** Appeared in [X]/5 topic searches

**Content Advantage:** [What they do better — be specific. Reference actual pages you crawled.]

**Content Gap:** [What they're missing — the target site's opportunity.]

**E-E-A-T Comparison:** [How their trust signals compare.]

---

### Competitor 2: [Domain]

[...same structure...]

---

### Competitor 3: [Domain]

[...same structure...]

---

## Section 3: Content Pillar Recommendations

### Pillar 1: [Title]

**Description:** [What this content pillar covers and why it matters]

| Axis | Score |
|------|-------|
| Relevance | High / Med / Low |
| Difficulty | High / Med / Low |
| Volume | High / Med / Low |
| **Opportunity** | **Priority [1/2/3]** |

**Recommended Articles:**

1. **[Article Title]** — [Intent: informational/commercial] — [Format: guide/comparison/case study] — [Quick Win / Long Play]
2. **[Article Title]** — [Intent] — [Format] — [Timeline]
3. **[Article Title]** — [Intent] — [Format] — [Timeline]

---

### Pillar 2: [Title]

[...same structure...]

---

[...repeat for all pillars...]
```

## Critical Rules for the Output

1. **Every single check gets its own section** — no exceptions, no skipping, no grouping
2. **"What it is" and "Why it matters" are copied word-for-word** from the reference files — this is the educational value of the report
3. **"Source" is the full citation** from the reference files — copied word-for-word
4. **"Observation" is specific** — cite specific pages, quote actual meta titles, describe what you found in the HTML. Never say "some pages have issues." Say which pages and what the issue is.
5. **"How to fix" is actionable** — give concrete alternatives. Don't say "add structured data." Say exactly what schema types to add to which page types.
6. **N/A checks are still listed** — show the check, mark N/A, and explain why
7. **Section grades count only applicable items** — N/A items excluded from denominator
8. **The horizontal rule `---` separates every check and every competitor** for clean readability
9. **Competitor analysis is based on actual SERP data** — you must run the WebSearches and cite real domains you found
10. **Content pillars must connect to observed gaps** — every recommendation should trace back to something found in Section 1 or Section 2
11. **Opportunity scoring follows the Goldilocks formula** — don't make all pillars Priority 1

## After Writing the File

After writing the `.md` file, output a brief terminal summary:

```
SEARCH GAP COMPLETE: [Company Name]
File: [filename].md ([total checks] checks, [X] competitors, [Y] pillars)

  Technical SEO         [grade]  (X/Y)
  E-E-A-T Signals       [grade]  (X/Y)
  Content Depth          [grade]  (X/Y)

  AUDIT OVERALL          [grade]  (X/Y passing)

  Top Competitors: [domain1], [domain2], [domain3]

  Content Pillars:
    P1: [pillar name]     Priority [X]
    P2: [pillar name]     Priority [X]
    P3: [pillar name]     Priority [X]

Open [filename].md for the full analysis.
```

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- **Crawl ALL blog posts** — this command requires full content inventory, not just a sample. For very large sites (50+ posts), cap at the 50 most recent.
- If Chrome is not installed, proceed with text-only analysis and note that visual checks may be less accurate
- If no blog section is found, note it and evaluate content checks based on available pages. This is itself a significant finding.
- The competitive analysis relies on WebSearch — search results may vary. Focus on pattern recognition (which domains appear repeatedly) rather than exact rankings.
- The `.md` file is the primary output — it should be a complete, standalone document that can be shared with a team
- The report should read as an educational document — someone who hasn't read the original sources should learn from reading this analysis
