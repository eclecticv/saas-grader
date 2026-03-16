---
description: Run 47 SaaS optimization rules against a website and display a scorecard with grades per section
argument-hint: <website-url>
allowed-tools: Read, Bash, WebFetch
---

# Command: audit

Analyze a SaaS website against 47 research-backed optimization rules and print results on screen.

## Usage
```
/saas-grader:audit <url>
```

## What It Does

1. **Follow the crawl & screenshot procedure** in `skills/saas-grader/reference/shared-procedures.md`
2. **Apply the scoring rules and grading scale** from the same shared procedures file
3. **Print results on screen** using the format below

## Output

**Print results directly on screen (do NOT write to a file).**

```
AUDIT: [Company Name] — [total pass]/[total applicable] passing ([overall grade])

  Brand & Messaging     [grade]  (X/Y)
  Page Design           [grade]  (X/Y)
  Pricing Plans         [grade]  (X/Y)
  Free Trials           [grade]  (X/Y)
  Freemium              [grade]  (X/Y)
  Churn Prevention      [grade]  (X/Y)
  Affiliates            [grade]  (X/Y)
  Referrals             [grade]  (X/Y)

CRITICAL:
  - [Rule ID]: [observation] → [fix]
  - [Rule ID]: [observation] → [fix]

WARNINGS:
  - [Rule ID]: [observation] → [fix]
  - [Rule ID]: [observation] → [fix]

Run /saas-grader:plan for prioritized fix strategy
Run /saas-grader:export for full detailed report
```

### Output Rules

1. **Scorecard first** — the summary table is the first thing the user sees
2. **CRITICAL section** — list the most impactful FAILs (above-the-fold, conversion-blocking items): BM-1, BM-2, BM-3, BM-6, BM-7, PD-5, PD-7, PD-11
3. **WARNINGS section** — list remaining FAILs grouped by severity, one line each
4. **Keep it scannable** — each finding is one line: Rule ID, what's wrong, what to do
5. **No file output** — everything goes to the terminal
6. **Include N/A counts** — note how many rules were N/A at the bottom if relevant
7. **Be specific in observations** — quote actual headlines, describe actual CTAs, cite real content
