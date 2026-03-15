# saas-grader

Score SaaS websites against 68 research-backed checks across conversion optimization and search discoverability. Every rule cites peer-reviewed research. No opinions.

## Install

```bash
claude /install eclecticv/saas-grader
```

Or load for a single session:
```bash
claude --plugin-dir /path/to/saas-grader
```

## Commands

| Command | Usage | What it does |
|---------|-------|-------------|
| **grade** | `/saas-grader:grade <url>` | 47-rule SaaS optimization audit |
| **search** | `/saas-grader:search <url>` | 21-check SEO audit + competitive landscape + content pillars |
| **wins** | `/saas-grader:wins <url>` | One-page prioritized summary (shareable) |
| **export** | `/saas-grader:export <url>` | Full combined report (68 checks + competitors + pillars) |

## What It Checks

### SaaS Optimization (47 rules)

| Category | Rules | Source |
|----------|-------|--------|
| Brand & Messaging | 8 | Journal of Marketing, Journal of Consumer Research |
| Page Design & Visuals | 14 | Marketing Science, Journal of Retailing |
| Pricing Plans | 9 | Journal of Consumer Psychology, Quarterly Journal of Economics |
| Free Trials | 4 | Management Science, Information Systems Research |
| Freemium | 2 | Journal of Marketing Research |
| Churn Prevention | 3 | Journal of the Academy of Marketing Science |
| Affiliates | 2 | International Journal of Research in Marketing |
| Referrals | 5 | Journal of Marketing, American Economic Review |

### Search Discoverability (21 checks)

| Category | Checks | Source |
|----------|--------|--------|
| Technical SEO | 8 | Google Search Central, web.dev, Moz |
| E-E-A-T Signals | 7 | Google Quality Rater Guidelines, Ahrefs |
| Content Depth | 6 | HubSpot, Backlinko, Content Marketing Institute |

### Competitive Landscape

The `search` and `export` commands also generate:
- Top 3 SERP competitors profiled with content gaps
- 3-5 scored content pillars with article recommendations
- Opportunity scoring (Relevance x Difficulty x Volume)

## Output Format

Every rule produces:
- **What it is** — from the reference (word for word)
- **Why it matters** — the research rationale
- **Source** — full citation (authors, journal, year)
- **Compliance** — PASS / FAIL / N/A
- **Observation** — what was found on the site
- **How to fix** — actionable recommendation (FAIL only)

## Requirements

- Claude Code CLI
- WebFetch (built-in)
- Chrome (optional, for homepage/pricing screenshots)

## License

MIT
