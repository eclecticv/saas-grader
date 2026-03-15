# Command: export

Run both the 47-rule SaaS optimization analysis and the 21-check search discoverability analysis, then produce a comprehensive combined markdown document. Designed as a systematic working document.

## Usage
```
/saas-grader:export <url>
```

## What It Does

1. **Run the full grade analysis internally** — follow all steps from the `grade` command (crawl homepage + pricing page, screenshot both, read all 4 saas-grader reference files, score all 47 rules)
2. **Run the full search analysis internally** — follow all steps from the `search` command (crawl all blog posts + product pages, read all 3 search-gap reference files, score all 21 checks, run competitive landscape, generate content pillars)
3. **Write the comprehensive combined analysis** to a single markdown file in the current directory

## Output

Write a markdown file to the current working directory named `[company-name-lowercase]-export.md`.

The file must follow this EXACT structure:

```markdown
# Full Analysis: [Company Name]

**URL:** [url]
**Date:** [date]
**Overall Score:** [total pass]/[total applicable] across 68 checks ([overall grade])

---

## Summary

| Section | Score | Grade |
|---------|-------|-------|
| **SaaS Optimization** | | |
| Brand & Messaging | X/Y | [grade] |
| Page Design & Visuals | X/Y | [grade] |
| Pricing Plans | X/Y | [grade] |
| Free Trials | X/Y | [grade] |
| Freemium | X/Y | [grade] |
| Churn Prevention | X/Y | [grade] |
| Affiliates | X/Y | [grade] |
| Referrals | X/Y | [grade] |
| **Search Discoverability** | | |
| Technical SEO | X/Y | [grade] |
| E-E-A-T Signals | X/Y | [grade] |
| Content Depth | X/Y | [grade] |

---

# Part 1: SaaS Optimization (47 Rules)

## 1. Brand & Messaging ([X/Y] — [Grade])

### BM-1: Productize Your Headline

**What it is:** [Copy from reference — word for word]

**Why it matters:** [Copy from reference — word for word]

**Source:** [Copy from reference — word for word]

**Compliance:** PASS | FAIL | N/A

**Observation:** [Specific observation]

**How to fix:** [Only if FAIL]

---

[...repeat for every rule through RF-5...]

# Part 2: Search Discoverability (21 Checks)

## 9. Technical SEO ([X/Y] — [Grade])

### TS-1: Schema.org Structured Data (JSON-LD)

[...same format as above...]

---

[...repeat through CD-6...]

# Part 3: Competitive Landscape

[...competitor profiles from search analysis...]

# Part 4: Content Pillar Recommendations

[...scored pillars with article recommendations...]
```

## Critical Rules for the Output

1. **Every single rule and check gets its own section** — all 68 items, no exceptions
2. **"What it is" and "Why it matters" are copied word-for-word** from the reference files
3. **"Source" is the full citation** from the reference files
4. **"Observation" is specific** — quote actual content from the site
5. **"How to fix" is actionable** — concrete alternatives, not vague advice
6. **N/A items are still listed** with explanations
7. **Section grades count only applicable items** — N/A excluded from denominator
8. **The horizontal rule `---` separates every rule/check**
9. **Parts are clearly labeled** with their own headers
10. **Section numbering is continuous** — SaaS sections 1-8, Search sections 9-11

## After Writing the File

After writing the `.md` file, output a brief terminal summary:

```
EXPORT COMPLETE: [Company Name]
File: [filename].md (68 checks evaluated)

  SaaS Optimization:
    Brand & Messaging     [grade]  (X/Y)
    Page Design           [grade]  (X/Y)
    Pricing Plans         [grade]  (X/Y)
    Free Trials           [grade]  (X/Y)
    Freemium              [grade]  (X/Y)
    Churn Prevention      [grade]  (X/Y)
    Affiliates            [grade]  (X/Y)
    Referrals             [grade]  (X/Y)

  Search Discoverability:
    Technical SEO         [grade]  (X/Y)
    E-E-A-T Signals       [grade]  (X/Y)
    Content Depth         [grade]  (X/Y)

  OVERALL               [grade]  (X/Y passing)

  Top Competitors: [domain1], [domain2], [domain3]

Open [filename].md for the full analysis.
```

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- The export file is the most comprehensive output — it covers all 68 checks plus competitive landscape and content pillars
- For a quick overview, use `/saas-grader:wins` instead
- For SaaS optimization only, use `/saas-grader:grade`
- For search analysis only, use `/saas-grader:search`
- If Chrome is not installed, proceed with text-only analysis
- The `.md` file should be a complete, standalone document suitable for systematic client work
