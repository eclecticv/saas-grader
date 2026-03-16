---
name: saas-grader
description: >
  This skill should be used when the user asks to audit, score, grade, or
  analyze a SaaS website, homepage, or pricing page. Triggers include
  "grade my SaaS site", "audit this homepage", "score my pricing page",
  "what's wrong with my landing page", "review my SaaS website against
  best practices", "run the 47-rule checklist", "export a SaaS optimization
  report", "how do I improve my SaaS homepage", "conversion optimization audit",
  "pricing page review", or "SaaS website teardown".
---

# SaaS Grader

A research-backed analysis tool that scores SaaS websites against 47 optimization rules drawn from peer-reviewed marketing science and UX research. Every rule includes the full research citation — no opinions, no fluff.

## Purpose

Analyze a SaaS homepage and pricing page against every rule in the playbook. For each rule, the output includes what it is, why it matters (the science), the source citation, a compliance verdict (PASS/FAIL/N/A), the specific observation, and a concrete fix recommendation if failing. The full analysis is exported as a standalone `.md` file.

## How It Works

1. **Crawl** the homepage via WebFetch (text content extraction)
2. **Find the pricing page** — detect pricing links in navigation and crawl if found
3. **Screenshot both pages** using local headless Chrome (full-page captures)
4. **Score every rule** — all 47 items, each as PASS, FAIL, or N/A
5. **Export** a comprehensive `.md` report covering every rule with full context

## The 47-Rule Checklist

### 1. Brand & Messaging (8 rules: BM-1 to BM-8)
Productized headline, top 3 benefits, present tense, newness signal, simple language, social proof numbers, 4-4.5 star rating, curated first testimonial.
> See [reference/brand-messaging.md](reference/brand-messaging.md)

### 2. Page Design & Visuals (14 rules: PD-1 to PD-14)
Design structure matches product type, brand-appropriate colors, layout adapted to SaaS type, moderate complexity, rounded CTAs, machine font, CTA upper-right, before/after left-to-right, video for exciting software, video speed, above-the-fold prioritization, content succinctness, scannable structure, signal-to-noise ratio.
> See [reference/page-design.md](reference/page-design.md)

### 3. Pricing Plans (9 rules: PR-1 to PR-9)
3-5 plans, decoy plan, left-to-right ordering, price below features, price-difference framing, simple pricing, easy math, flat+usage hybrid, flat-rate option.
> See [reference/pricing-plans.md](reference/pricing-plans.md)

### 4. Free Trials (4 rules: FT-1 to FT-4)
Full-feature trial, 7-day length, high trial usage, extensions over discounts.
> See [reference/growth-levers.md](reference/growth-levers.md)

### 5. Freemium (2 rules: FM-1 to FM-2)
Usage-limited freemium, freemium decoy plan.
> See [reference/growth-levers.md](reference/growth-levers.md)

### 6. Churn Prevention (3 rules: CP-1 to CP-3)
Customer gifts, auto-enrolling loyalty program, generous downgrades.
> See [reference/growth-levers.md](reference/growth-levers.md)

### 7. Affiliates (2 rules: AF-1 to AF-2)
Optimize affiliate payment model, protect from deceptive affiliates.
> See [reference/growth-levers.md](reference/growth-levers.md)

### 8. Referrals (5 rules: RF-1 to RF-5)
Altruistic framing, pre-filled messages, avoid money rewards, keep rewards small, targeted referrals.
> See [reference/growth-levers.md](reference/growth-levers.md)

## Scoring

Each section receives a letter grade (A+ through F) based on the percentage of applicable items that pass. N/A items are excluded from the denominator. See `reference/shared-procedures.md` for the full grading scale, scoring rules, and crawl/screenshot procedure.

## Output Format

For each of the 47 rules, the `.md` report includes:
- **What it is** — description of the rule (from the reference)
- **Why it matters** — the science behind it (from the reference)
- **Source** — full research citation with authors, journal, date, and universities
- **Compliance** — PASS, FAIL, or N/A
- **Observation** — what was specifically observed on the site
- **How to fix** — concrete, actionable recommendation (only if FAIL)

