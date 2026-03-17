# saas-grader

Score SaaS websites against 47 research-backed optimization rules from peer-reviewed marketing science. Every rule cites its source. No opinions.

## Install

```bash
claude /install saas-grader@andorlabs
```

Or load for a single session:
```bash
claude --plugin-dir /path/to/saas-grader
```

## Commands

| Command | Usage | What it does |
|---------|-------|-------------|
| **audit** | `/saas-grader:audit <url>` | Run 47 rules, print scorecard + findings on screen |
| **plan** | `/saas-grader:plan <url>` | Generate prioritized fix strategy (critical/medium/low) |
| **export** | `/saas-grader:export <url>` | Write full 47-rule detailed report to markdown file |

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
