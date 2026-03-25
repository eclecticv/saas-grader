---
description: Run 47 SaaS optimization rules against a website — prints scorecard to terminal and writes full report to file
argument-hint: <website-url>
allowed-tools: Read, Write, Bash, WebFetch
---

# Command: saas

Analyze a SaaS website against 47 research-backed optimization rules. Prints a high-level scorecard with prioritized fixes to the terminal, then writes a comprehensive `.md` report to disk.

## Usage
```
/saas-grader:saas <url>
```

## What It Does

1. **Follow the crawl & screenshot procedure** in `skills/saas-grader/reference/shared-procedures.md`
2. **Apply the scoring rules and grading scale** from the same shared procedures file
3. **Print the terminal summary** (see Terminal Output below)
4. **Write the full report** to `~/Desktop/claude-code/[company]-saas-report.md` (see File Output below)

---

## Terminal Output

Print this to the terminal first:

```
SAAS AUDIT: [Company Name] — [total pass]/[total applicable] passing ([overall grade])

  Brand & Messaging     [grade]  (X/Y)
  Page Design           [grade]  (X/Y)
  Pricing Plans         [grade]  (X/Y)
  Free Trials           [grade]  (X/Y)
  Freemium              [grade]  (X/Y)
  Churn Prevention      [grade]  (X/Y)
  Affiliates            [grade]  (X/Y)
  Referrals             [grade]  (X/Y)

━━━ CRITICAL — Fix This Week ━━━

1. [Rule ID]: [Rule Name]
   Problem: [One-sentence observation — quote the actual headline, CTA, etc.]
   Fix: [Specific, actionable recommendation with a concrete example]
   Impact: [Why this matters — cite the research effect size]

━━━ MEDIUM — Fix This Month ━━━

2. [Rule ID]: [Rule Name]
   Problem: [observation]
   Fix: [recommendation]

━━━ LOW — Backlog ━━━

3. [Rule ID]: [Rule Name]
   Problem: [observation]
   Fix: [recommendation]

━━━ TOP WINS (What's Working) ━━━

- [Rule ID]: [What they're doing well — be specific]

Full report: ~/Desktop/claude-code/[company]-saas-report.md
```

### Terminal Output Rules

1. **Scorecard first** — the summary table is the first thing the user sees
2. **Only include FAILs** in the fix tiers — do not list PASSes or N/As
3. **Critical tier gets full detail** — Problem + Fix + Impact
4. **Medium and Low tiers get Problem + Fix** — keep concise
5. **Top Wins section** — 3-5 strongest PASSes to show what's working
6. **Be specific** — quote actual headlines, describe actual CTAs, cite real content
7. **If a tier has no FAILs, omit it**

### Priority Classification

**Critical (Fix This Week)** — above the fold, directly block conversion, strongest research effect sizes:
- BM-1, BM-2, BM-3, BM-6, BM-7, PD-5, PD-7, PD-11

**Medium (Fix This Month)** — affect conversion but below fold or moderate effect sizes:
- PD-1, PD-2, PD-3, PD-4, PD-8, PD-9, PD-12, PD-13, PD-14
- PR-1 through PR-9, BM-8, FT-1, FT-3, FM-1, FM-2

**Low (Backlog)** — less visible, harder to observe, smaller effect sizes:
- BM-4, BM-5, PD-6, PD-10, RF-1 through RF-5, AF-1, AF-2, CP-1 through CP-3, FT-2, FT-4

Use judgment for edge cases — promote egregiously bad items.

---

## File Output

Write to `~/Desktop/claude-code/[company]-saas-report.md` with this EXACT structure:

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

**What it is:** [Copy from reference — word for word]

**Why it matters:** [Copy from reference — word for word]

**Source:** [Copy full citation from reference — word for word]

**Recommendation:** [Copy from reference — word for word]

**Compliance:** PASS | FAIL | N/A

**Observation:** [What you actually observed — quote headlines, describe CTAs, cite evidence]

**How to fix:** [Only if FAIL. Specific, actionable.]

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

### File Output Rules

1. **Every single rule gets its own section** — no exceptions, no skipping, no grouping
2. **"What it is", "Why it matters", and "Recommendation" are copied word-for-word** from the reference files
3. **"Source" is the full citation** from the reference files
4. **"Observation" is specific** — never say "vague headline." Say what the headline actually says.
5. **"How to fix" is actionable** — give a concrete alternative, not vague advice
6. **N/A rules are still listed** — show the rule, mark N/A, and explain why
7. **Section grades count only applicable items** — N/A items excluded from denominator
8. **The horizontal rule `---` separates every rule** for clean readability
