# SaaS Grader

A research-backed analysis tool that scores SaaS websites against 47 optimization rules drawn from peer-reviewed marketing science and UX research. Every rule includes the full research citation — no opinions, no fluff.

Rules drawn from peer-reviewed marketing science and UX research, supplemented with Nielsen Norman Group eyetracking studies.

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

Each section receives a letter grade (A+ through F) based on the percentage of applicable items that pass:

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

Items marked N/A are excluded from the denominator.

## Output Format

For each of the 47 rules, the `.md` report includes:
- **What it is** — description of the rule (from the reference)
- **Why it matters** — the science behind it (from the reference)
- **Source** — full research citation with authors, journal, date, and universities
- **Compliance** — PASS, FAIL, or N/A
- **Observation** — what was specifically observed on the site
- **How to fix** — concrete, actionable recommendation (only if FAIL)

## Research Sources

All rules are drawn from peer-reviewed research published in journals including:
- Journal of Marketing, Journal of Marketing Research, Journal of Consumer Research
- Marketing Science, Management Science
- Journal of Business Research, International Journal of Research in Marketing
- Journal of Consumer Psychology, Journal of Service Research
- Information Systems Research, International Journal of Advertising
- Business Horizons, Proceedings of the Human Factors and Ergonomics Society

Research conducted at institutions including: UCLA, Stanford, MIT Sloan, University of Melbourne, National University of Singapore, University of Washington, Georgetown University, University of South Florida, University of British Columbia, Nielsen Norman Group, Babson College, University of Miami, Bentley University, Oklahoma State University, University of Florida, Fudan University, Oregon State University, Princeton University, and many others.
