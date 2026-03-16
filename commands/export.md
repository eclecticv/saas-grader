---
description: Write a full 47-rule SaaS optimization report to a markdown file with every rule documented
argument-hint: <website-url>
allowed-tools: Read, Write, Bash, WebFetch
---

# Command: export

Run the 47-rule SaaS optimization analysis and produce a comprehensive markdown report covering every single rule.

## Usage
```
/saas-grader:export <url>
```

## What It Does

1. **Follow the crawl & screenshot procedure** in `skills/saas-grader/reference/shared-procedures.md`
2. **Apply the scoring rules and grading scale** from the same shared procedures file
3. **Write the full analysis** to a markdown file in the current directory

## Output

Write a markdown file to the current working directory named `[company]-saas-export.md` (see shared-procedures.md for company name extraction).

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

**How to fix:** [Only if FAIL. Specific, actionable recommendation based on what was observed.]

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
2. **"What it is" and "Why it matters" are copied word-for-word** from the reference files
3. **"Source" is the full citation** from the reference files
4. **"Observation" is specific** — never say "vague headline." Say what the headline actually says.
5. **"How to fix" is actionable** — give a concrete alternative, not vague advice
6. **N/A rules are still listed** — show the rule, mark N/A, and explain why
7. **Section grades count only applicable items** — N/A items excluded from denominator
8. **The horizontal rule `---` separates every rule** for clean readability

## After Writing the File

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
