# Shared Procedures

Common procedures used by the `/saas-grader:saas` command.

## Crawl & Screenshot Procedure

1. **Crawl the homepage** via WebFetch to extract text content (if the page content exceeds 50KB, work with the first 50KB only)
2. **Find the pricing page** — look for pricing/plans links in the navigation or page content. If found, crawl it too via WebFetch (same 50KB limit)
3. **Screenshot the homepage only** using local headless Chrome (NOT the browser MCP, which runs in Docker and may not be available):
   - First, find the Chrome binary: `which google-chrome-stable 2>/dev/null || which google-chrome 2>/dev/null || which chromium 2>/dev/null || ls "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" 2>/dev/null`
   - Screenshot the homepage with 30-second timeout and memory limits (macOS-compatible):
     ```bash
     ( "/path/to/chrome" --headless=new --disable-gpu --no-sandbox --disable-extensions --disable-background-networking --disable-sync --disable-translate --disable-default-apps --js-flags="--max-old-space-size=256" --screenshot="[company]-homepage.png" --window-size=1280,900 "[url]" 2>/dev/null & CHROME_PID=$!; ( sleep 30 && kill $CHROME_PID 2>/dev/null ) & WATCHDOG=$!; wait $CHROME_PID 2>/dev/null; kill $WATCHDOG 2>/dev/null ); if [ ! -f "[company]-homepage.png" ]; then echo "Screenshot failed or timed out — proceeding with text-only analysis"; fi
     ```
   - If the screenshot file exists, read it using the Read tool to visually inspect the above-the-fold area, then delete it
   - **If the screenshot failed or timed out, skip it entirely** — do NOT retry. Proceed with text-only analysis
   - **Do NOT screenshot the pricing page** — text analysis from WebFetch is sufficient for pricing rules
4. **Read reference files in batches as you score each section** (do NOT load all 8 at once):
   - Score Brand & Messaging → read `skills/saas-grader/reference/brand-messaging.md` (BM-1 to BM-8)
   - Score Page Design → read `skills/saas-grader/reference/page-design.md` (PD-1 to PD-14)
   - Score Pricing Plans → read `skills/saas-grader/reference/pricing-plans.md` (PR-1 to PR-9)
   - Score Free Trials → read `skills/saas-grader/reference/free-trials.md` (FT-1 to FT-4)
   - Score Freemium → read `skills/saas-grader/reference/freemium.md` (FM-1 to FM-2)
   - Score Churn Prevention → read `skills/saas-grader/reference/churn-prevention.md` (CP-1 to CP-3)
   - Score Affiliates → read `skills/saas-grader/reference/affiliates.md` (AF-1 to AF-2)
   - Score Referrals → read `skills/saas-grader/reference/referrals.md` (RF-1 to RF-5)
5. **Score every single rule** as PASS, FAIL, or N/A based on what you observed

## Scoring Rules

- Score each applicable item as PASS or FAIL based on the criteria in the reference files
- Mark items as N/A ONLY when they genuinely don't apply (e.g., "video speed" when there's no video, "freemium decoy" when there's no freemium model, "referral framing" when there's no referral program)
- N/A items are excluded from the pass rate — they don't count against the score
- Be honest and specific — cite what you actually observed on the site
- When uncertain, lean toward FAIL with a note about what you couldn't verify
- For items marked N/A, still include them in the output but note why they don't apply

## Rigor Protocol

Before finalizing any PASS score, argue the other side:

1. **Re-read the FAIL criteria** — does any bullet point apply, even partially?
2. **Apply the "stranger test"** — would a first-time visitor with no industry knowledge understand this? Don't project your own familiarity onto the visitor.
3. **Separate headline from page** — if the headline alone doesn't pass but supporting copy below the fold does, note the gap. The headline carries most of the weight because most visitors never scroll.
4. **Watch for borrowed positioning** — "X for Y" comparisons ("Superhuman for X," "Figma for Y") are a common pattern that can mask weak self-description. Evaluate whether messaging stands on its own without the comparison.
5. **No cheerleading** — observations should be analytical, not congratulatory. Note what works AND what's weak, even on passing items. Every observation should include what could be stronger.

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
- **IMPORTANT: Use `--headless=new` and `--window-size=1280,900`** — never use heights above 900px. Larger screenshots cause excessive memory usage.
- **Memory safety:** The screenshot command has a 30-second timeout and 256MB JS heap limit. If it fails, times out, or produces no file, proceed with text-only analysis. Never retry a failed screenshot. Text analysis via WebFetch is the primary data source — the screenshot is supplementary for visual layout checks only.
- If Chrome is not installed or screenshots fail, proceed with text-only analysis. These rules require visual inspection and should be scored with reduced confidence (note in observation): PD-1, PD-2, PD-5, PD-6, PD-7, PD-8, PD-11. Other PD rules (PD-3, PD-4, PD-9, PD-10, PD-12, PD-13, PD-14) can be adequately assessed from text content alone
- If no pricing page is found, note it and score pricing items as N/A where they require pricing page content
