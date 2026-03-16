# Command: plan

Run the 47-rule SaaS optimization analysis, then generate a prioritized fix strategy on screen.

## Usage
```
/saas-grader:plan <url>
```

## What It Does

1. **Run the full audit internally** — follow all steps from the `audit` command (crawl homepage + pricing page, screenshot both, read all 4 saas-grader reference files, score all 47 rules)
2. **Classify every FAIL into priority tiers** based on the criteria below
3. **Generate a prioritized fix strategy** with actionable recommendations
4. **Print the strategy on screen**

## Priority Classification

### Critical (Fix This Week)
Items that are above the fold, directly block conversion, or have the strongest research effect sizes:
- Headline/positioning misses (BM-1)
- No social proof or trust signals above the fold (BM-6, BM-7)
- CTA missing or poorly placed (PD-5, PD-7, PD-11)
- Value proposition unclear (BM-2, BM-3)

### Medium (Fix This Month)
Items that affect conversion but are below the fold or have moderate effect sizes:
- Design-product mismatch (PD-1, PD-2, PD-3)
- Pricing structure issues (PR-1, PR-2, PR-3, PR-6)
- Content structure problems (PD-12, PD-13, PD-14)
- Missing before/after framing (PD-8)
- Testimonial quality (BM-8)

### Low (Backlog)
Items that are less visible, harder to observe, or have smaller effect sizes:
- Font choices (PD-6)
- Video speed (PD-10)
- Referral framing details (RF-1 through RF-5)
- Affiliate structure (AF-1, AF-2)
- Churn prevention signals (CP-1, CP-2, CP-3)
- Trial length optimization (FT-2, FT-4)

## Output

**Print results directly on screen (do NOT write to a file).**

Display the following format in the terminal:

```
FIX STRATEGY: [Company Name]
Score: [total pass]/[total applicable] ([overall grade]) across 47 checks

━━━ CRITICAL — Fix This Week ━━━

1. [Rule ID]: [Rule Name]
   Problem: [One-sentence observation with specifics — quote the actual headline, CTA, etc.]
   Fix: [Specific, actionable recommendation with a concrete example]
   Impact: [Why this matters — cite the research effect size]

2. [Rule ID]: [Rule Name]
   Problem: [observation]
   Fix: [recommendation]
   Impact: [rationale]

━━━ MEDIUM — Fix This Month ━━━

3. [Rule ID]: [Rule Name]
   Problem: [observation]
   Fix: [recommendation]

4. [Rule ID]: [Rule Name]
   Problem: [observation]
   Fix: [recommendation]

━━━ LOW — Backlog ━━━

5. [Rule ID]: [Rule Name]
   Problem: [observation]
   Fix: [recommendation]

━━━ TOP WINS (What's Working) ━━━

- [Rule ID]: [What they're doing well — be specific]
- [Rule ID]: [What they're doing well]
- [Rule ID]: [What they're doing well]

Run /saas-grader:export for the full 47-rule detailed report
```

### Output Rules

1. **Only include FAILs** in the fix sections — do not list PASSes or N/As
2. **Critical tier gets full detail** — Problem + Fix + Impact for each item
3. **Medium tier gets Problem + Fix** — skip Impact to keep it concise
4. **Low tier gets Problem + Fix** — one-liner each
5. **Top Wins section** — 3-5 strongest PASSes to show what's working
6. **Be specific in fixes** — don't say "improve headline." Say what the headline should say instead
7. **Include the rule ID** so the reader can cross-reference with the export
8. **Number the items** within each tier for easy reference
9. **If a tier has no FAILs, omit that section**
10. **No file output** — everything goes to the terminal

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- If Chrome is not installed, proceed with text-only analysis
- Priority classification is a guideline — use judgment for edge cases (e.g., if a "medium" item is egregiously bad, promote it to critical)
- The strategy should be a working document — someone should be able to hand it to a designer/developer and say "do these in order"
