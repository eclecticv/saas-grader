# Command: export

Run the 47-rule SaaS optimization analysis and produce a comprehensive markdown report covering every single rule.

## Usage
```
/saas-grader:export <url>
```

## What It Does

1. **Crawl the homepage** via WebFetch to extract text content
2. **Find the pricing page** — look for pricing/plans links in the navigation or page content. If found, crawl it too via WebFetch
3. **Screenshot both pages** using local headless Chrome (NOT the browser MCP, which runs in Docker and may not be available):
   - First, find the Chrome binary: `which google-chrome-stable 2>/dev/null || which google-chrome 2>/dev/null || which chromium 2>/dev/null || ls "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" 2>/dev/null`
   - Screenshot the homepage: `"/path/to/chrome" --headless --disable-gpu --no-sandbox --screenshot="[company]-homepage.png" --window-size=1280,4000 "[url]"`
   - If a pricing page was found, screenshot it too: `"/path/to/chrome" --headless --disable-gpu --no-sandbox --screenshot="[company]-pricing.png" --window-size=1280,4000 "[pricing-url]"`
   - Read the screenshot files using the Read tool to visually inspect them
   - Delete the screenshot files after inspection
4. **Read all 4 reference files** to get the full checklist:
   - `skills/saas-grader/reference/brand-messaging.md` (BM-1 to BM-8)
   - `skills/saas-grader/reference/page-design.md` (PD-1 to PD-14)
   - `skills/saas-grader/reference/pricing-plans.md` (PR-1 to PR-9)
   - `skills/saas-grader/reference/growth-levers.md` (FT-1 to FT-4, FM-1 to FM-2, CP-1 to CP-3, AF-1 to AF-2, RF-1 to RF-5)
5. **Score every single rule** as PASS, FAIL, or N/A based on what you observed
6. **Write the full analysis** to a markdown file in the current directory

## Scoring Rules

- Score each applicable item as PASS or FAIL based on the criteria in the reference files
- Mark items as N/A ONLY when they genuinely don't apply (e.g., "video speed" when there's no video, "freemium decoy" when there's no freemium model, "referral framing" when there's no referral program)
- N/A items are excluded from the pass rate — they don't count against the score
- Be honest and specific — cite what you actually observed on the site
- When uncertain, lean toward FAIL with a note about what you couldn't verify
- For items marked N/A, still include them in the output but note why they don't apply

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

Write a markdown file to the current working directory named `[company-name-lowercase]-saas-export.md`.

The file must follow this EXACT structure:

```markdown
# SaaS Optimization Report: [Company Name]

**URL:** [url]
**Date:** [date]
**Overall Score:** [total pass]/[total applicable] ([overall grade])

---

## Summary

| Section | Score | Grade |
|---------|-------|-------|
| Brand & Messaging | X/Y | [grade] |
| Page Design & Visuals | X/Y | [grade] |
| Pricing Plans | X/Y | [grade] |
| Free Trials | X/Y | [grade] |
| Freemium | X/Y | [grade] |
| Churn Prevention | X/Y | [grade] |
| Affiliates | X/Y | [grade] |
| Referrals | X/Y | [grade] |

---

## 1. Brand & Messaging ([X/Y] — [Grade])

### BM-1: Productize Your Headline

**What it is:** [Copy the "What it is" text from the reference file — word for word]

**Why it matters:** [Copy the "Why it matters" text from the reference file — word for word]

**Source:** [Copy the full "Source" citation from the reference file — word for word]

**Compliance:** PASS | FAIL | N/A

**Observation:** [What you actually observed on the site — be specific. Quote the actual headline, describe what you saw, cite evidence.]

**How to fix:** [Only if FAIL. Specific, actionable recommendation based on what was observed. Reference the research. Example: "Rewrite the headline from 'Transform your workflow' to something specific like 'Automated invoice processing — from receipt to ledger in 30 seconds.'"]

---

[...repeat for every rule in the section...]

## 2. Page Design & Visuals ([X/Y] — [Grade])

[...every PD rule...]

## 3. Pricing Plans ([X/Y] — [Grade])

[...every PR rule...]

## 4. Free Trials ([X/Y] — [Grade])

[...every FT rule...]

## 5. Freemium ([X/Y] — [Grade])

[...every FM rule...]

## 6. Churn Prevention ([X/Y] — [Grade])

[...every CP rule...]

## 7. Affiliates ([X/Y] — [Grade])

[...every AF rule...]

## 8. Referrals ([X/Y] — [Grade])

[...every RF rule...]
```

## Critical Rules for the Output

1. **Every single rule gets its own section** — no exceptions, no skipping, no grouping
2. **"What it is" and "Why it matters" are copied word-for-word** from the reference files — this is the educational value of the report
3. **"Source" is the full citation** from the reference files — authors, paper title, journal, date, universities
4. **"Observation" is specific** — never say "vague headline." Say what the headline actually says. Never say "no social proof." Say what IS on the page and what's missing.
5. **"How to fix" is actionable** — give a concrete alternative. Don't say "improve your headline." Say exactly what the headline should say instead.
6. **N/A rules are still listed** — show the rule, mark N/A, and explain why (e.g., "N/A — no video present on the homepage")
7. **Section grades count only applicable items** — N/A items excluded from denominator
8. **The horizontal rule `---` separates every rule** for clean readability

## After Writing the File

After writing the `.md` file, output a brief terminal summary:

```
EXPORT COMPLETE: [Company Name]
File: [filename]-saas-export.md (47 rules evaluated)

  Brand & Messaging     [grade]  (X/Y)
  Page Design           [grade]  (X/Y)
  Pricing Plans         [grade]  (X/Y)
  Free Trials           [grade]  (X/Y)
  Freemium              [grade]  (X/Y)
  Churn Prevention      [grade]  (X/Y)
  Affiliates            [grade]  (X/Y)
  Referrals             [grade]  (X/Y)

  OVERALL               [grade]  (X/Y passing)

Open [filename]-saas-export.md for the full analysis.
```

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- If Chrome is not installed, proceed with text-only analysis and note that visual checks (PD items) may be less accurate
- If no pricing page is found, note it and score pricing items as N/A where they require pricing page content
- The `.md` file is the primary output — it should be a complete, standalone document that can be shared with a team
- The report should read as an educational document — someone who hasn't read the original playbook should learn from reading this analysis
