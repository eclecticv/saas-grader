# Shared Procedures

Common procedures used by all saas-grader commands (audit, plan, export).

## Crawl & Screenshot Procedure

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

## Company Name Extraction

Extract the company name from the page title or domain, using the brand name only (e.g., for `https://www.acme.com`, use `acme`; for a page titled "Acme - Project Management", use `acme`).

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- If Chrome is not installed, proceed with text-only analysis and note that visual checks (PD items) may be less accurate
- If no pricing page is found, note it and score pricing items as N/A where they require pricing page content
