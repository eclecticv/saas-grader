# Technical SEO (TS-1 to TS-8)

## TS-1: Schema.org Structured Data (JSON-LD)

**What it is:** The site implements Schema.org structured data using JSON-LD format to help search engines understand page content, organization details, and content relationships.

**Recommendation:** Add JSON-LD structured data to every key page. At minimum, implement Organization schema on the homepage, Article/BlogPosting schema on blog posts, and FAQPage schema where applicable. JSON-LD is Google's preferred format. Structured data enables rich results (star ratings, FAQ dropdowns, breadcrumbs) that increase click-through rates by up to 30%.

**Why it matters:** Search engines use structured data to understand the meaning and relationships of content. Pages with structured data are eligible for rich results — enhanced SERP features like FAQ accordions, star ratings, and knowledge panels — which dramatically increase visibility and CTR. Without it, your pages compete on title and description alone.

**Key stat:** Rich results from structured data can increase click-through rates by up to 30%.

**Source:** Google Search Central. "Understand how structured data works." Google Developers Documentation (2024). Supplemented by: Moz. "The Beginner's Guide to Structured Data" (2023). Also: web.dev. "Structured data" guidelines (2024).

**PASS criteria:**
- JSON-LD structured data present on the homepage (Organization or WebSite schema)
- Blog posts include Article or BlogPosting schema with author, datePublished, dateModified
- Schema validates without errors in Google's Rich Results Test

**FAIL criteria:**
- No structured data on any page
- Only Microdata or RDFa used (not JSON-LD, Google's preferred format)
- Structured data present but contains errors or incomplete required fields

**N/A when:** The site is a single landing page with no blog or content section.

---

## TS-2: Meta Title Optimization

**What it is:** Every page has a unique, descriptive meta title under 60 characters that includes the primary keyword near the front and accurately represents the page content.

**Recommendation:** Write unique meta titles for every page. Keep them under 60 characters to avoid truncation in SERPs. Place the primary keyword within the first 3-4 words. Follow a consistent format like "[Primary Keyword] — [Brand]" or "[Primary Keyword]: [Supporting Detail] | [Brand]". Never duplicate titles across pages.

**Why it matters:** The meta title is the single most important on-page SEO element. It is the first thing users see in search results and the strongest relevance signal to search engines. Truncated, duplicated, or keyword-stuffed titles reduce both rankings and click-through rates.

**Key stat:** Pages with optimized title tags rank on average 3.5 positions higher than those with generic titles.

**Source:** Google Search Central. "Influence your title links in search results." Google Developers Documentation (2024). Also: Moz. "Title Tag" — Moz SEO Learning Center (2023). Supplemented by: Ahrefs. "How to Craft the Perfect SEO Title Tag" (2023).

**PASS criteria:**
- Every crawled page has a unique meta title
- Titles are under 60 characters (no truncation in SERPs)
- Primary keyword appears within the first 3-4 words
- Title accurately describes the page content

**FAIL criteria:**
- Duplicate meta titles across multiple pages
- Titles exceed 60 characters and get truncated
- Generic titles like "Home" or "Blog" without descriptive keywords
- Primary keyword absent or buried at the end of the title

---

## TS-3: Meta Description Quality

**What it is:** Every page has a unique, compelling meta description between 120-160 characters that summarizes the page content and includes a call to action or value proposition.

**Recommendation:** Write unique meta descriptions for every page. Keep them between 120-160 characters. Include the target keyword naturally. Add a call-to-action or clear value proposition. Think of descriptions as ad copy — they don't directly affect rankings, but they significantly affect click-through rates from SERPs.

**Why it matters:** While meta descriptions are not a direct ranking factor, they are the primary "ad copy" that appears under your title in search results. A compelling description increases CTR, which is a user engagement signal that indirectly influences rankings. Missing descriptions let Google auto-generate snippets that may not represent your page well.

**Key stat:** Pages with custom meta descriptions have 5.8% higher CTR than those without.

**Source:** Google Search Central. "Control your snippets in search results." Google Developers Documentation (2024). Also: Ahrefs. "How to Write the Perfect Meta Description" (2023). Supplemented by: Backlinko. "Google CTR Stats" — analysis of 5 million search results (2023).

**PASS criteria:**
- Every crawled page has a unique meta description
- Descriptions are between 120-160 characters
- Target keyword appears naturally in the description
- Description includes a value proposition or call to action

**FAIL criteria:**
- Missing meta descriptions on key pages
- Duplicate descriptions across multiple pages
- Descriptions under 70 characters or over 160 characters
- Keyword-stuffed or robotic descriptions that don't read naturally

---

## TS-4: Heading Hierarchy

**What it is:** Each page has exactly one H1 tag, followed by a logical hierarchy of H2-H6 headings with no skipped levels, creating a clear content outline.

**Recommendation:** Use exactly one H1 per page that describes the page's primary topic. Structure subheadings as H2s, with H3s nested beneath them where needed. Never skip heading levels (e.g., jumping from H2 to H4). Headings should form a readable outline of the page — if you extracted just the headings, the page structure should be clear.

**Why it matters:** Search engines use heading hierarchy to understand content structure and topic relationships. A clean heading structure helps crawlers identify the primary topic (H1), subtopics (H2s), and supporting details (H3+). Screen readers also rely on heading hierarchy for navigation, so it's both an SEO and accessibility concern.

**Key stat:** Pages with proper H1-H6 hierarchy correlate with 0.3 positions higher rankings on average.

**Source:** Google Search Central. "Google Search Essentials — Key best practices." Google Developers Documentation (2024). Also: web.dev. "Headings and landmarks" — accessibility guidelines (2024). Supplemented by: Moz. "On-Page Ranking Factors" (2023).

**PASS criteria:**
- Exactly one H1 per page containing the primary topic/keyword
- Logical H2-H6 hierarchy with no skipped levels
- Headings form a readable content outline
- H1 is not the site logo or brand name alone (on content pages)

**FAIL criteria:**
- Multiple H1 tags on a single page
- Missing H1 tag entirely
- Skipped heading levels (H2 followed by H4, no H3)
- Headings used for visual styling rather than content structure

---

## TS-5: Internal Linking Structure

**What it is:** The site has a robust internal linking structure with contextual anchor text, no orphan pages, and key pages reachable within 3 clicks from the homepage.

**Recommendation:** Link related content pages to each other using descriptive anchor text (not "click here" or "read more"). Ensure every page is reachable within 3 clicks from the homepage. Blog posts should link to related posts, and product pages should link to relevant case studies or resources. Use a hub-and-spoke or pillar-cluster model for topical content.

**Why it matters:** Internal links distribute page authority (PageRank) throughout the site and help search engines discover and understand content relationships. Pages with more internal links pointing to them tend to rank higher. Orphan pages (no internal links) may never get crawled or indexed. Descriptive anchor text also provides relevance signals for the linked page.

**Key stat:** Pages with strong internal linking receive 40% more organic traffic on average.

**Source:** Google Search Central. "Links best practices." Google Developers Documentation (2024). Also: Ahrefs. "Internal Links for SEO: An Actionable Guide" (2023). Supplemented by: Moz. "Internal Links" — Moz SEO Learning Center (2023).

**PASS criteria:**
- Key pages reachable within 3 clicks from the homepage
- Blog posts link to related posts with descriptive anchor text
- Product/feature pages cross-link to relevant resources
- No orphan pages discovered (all pages linked from at least one other page)

**FAIL criteria:**
- Orphan pages with no internal links pointing to them
- Generic anchor text ("click here", "read more", "learn more") used predominantly
- Blog posts have no internal links to related content
- Key pages buried more than 4 clicks deep from homepage

---

## TS-6: Image Optimization

**What it is:** All images have descriptive alt text, use meaningful filenames, and implement lazy loading for below-the-fold images to improve both accessibility and search visibility.

**Recommendation:** Add descriptive alt text to every meaningful image — describe what the image shows and include relevant keywords naturally. Use descriptive filenames (e.g., `dashboard-analytics-overview.png` not `IMG_3847.png`). Implement lazy loading on below-the-fold images to improve page speed. Use modern formats (WebP, AVIF) where possible.

**Why it matters:** Google Image Search drives significant traffic. Alt text is the primary way search engines understand image content. Descriptive filenames provide an additional relevance signal. Missing alt text also creates accessibility barriers for screen reader users. Image optimization directly impacts Core Web Vitals scores (LCP in particular).

**Key stat:** Google Images accounts for 22.6% of all web searches. Proper alt text increases image search traffic by 10-15%.

**Source:** Google Search Central. "Google image SEO best practices." Google Developers Documentation (2024). Also: web.dev. "Image performance" — Core Web Vitals guidelines (2024). Supplemented by: Moz. "Image SEO: How to Optimize Images for Search" (2023).

**PASS criteria:**
- All meaningful images have descriptive alt text (not empty or generic)
- Image filenames are descriptive (not random strings or camera defaults)
- Below-the-fold images use lazy loading (`loading="lazy"`)
- Images use modern formats (WebP, AVIF) or are reasonably compressed

**FAIL criteria:**
- Multiple images missing alt text or using empty alt on non-decorative images
- Generic filenames like `image1.png`, `screenshot.png`, `IMG_3847.jpg`
- No lazy loading on image-heavy pages
- Excessively large image files (>500KB for non-hero images)

---

## TS-7: Canonical Tags & URL Structure

**What it is:** Every page has a self-referencing canonical tag, URLs are clean and descriptive, and there are no duplicate content issues from parameter variations or trailing slashes.

**Recommendation:** Add self-referencing canonical tags to every page. Use clean, descriptive URLs (e.g., `/blog/pricing-strategy-guide` not `/blog/?p=4827`). Ensure consistency with trailing slashes — pick one format and redirect the other. Prevent duplicate content from URL parameters by setting canonical tags or using parameter handling in Search Console.

**Why it matters:** Without canonical tags, search engines may split ranking signals across duplicate versions of the same page (www vs non-www, HTTP vs HTTPS, parameter variations). This dilutes page authority and can cause indexing issues. Clean URLs also provide a minor ranking signal and improve user experience when URLs are visible in SERPs.

**Key stat:** Proper canonicalization can consolidate ranking signals by up to 20% for pages with duplicate variations.

**Source:** Google Search Central. "Consolidate duplicate URLs with canonicals." Google Developers Documentation (2024). Also: Moz. "Canonical URL Tag — The Most Important Advancement in SEO Practices Since Sitemaps" (2023). Supplemented by: Ahrefs. "Canonical Tags: A Simple Guide for Beginners" (2023).

**PASS criteria:**
- Self-referencing canonical tags present on all key pages
- Clean, descriptive URLs without unnecessary parameters or IDs
- Consistent trailing slash handling (no duplicate URLs)
- No duplicate content issues from parameter variations

**FAIL criteria:**
- Missing canonical tags on key pages
- Messy URLs with query parameters, session IDs, or numeric-only slugs
- Both `/page` and `/page/` resolving without redirect
- Multiple URL versions of the same content without canonicalization

---

## TS-8: Open Graph & Twitter Card Metadata

**What it is:** Every page includes Open Graph (og:) and Twitter Card meta tags with appropriate title, description, and image so content renders correctly when shared on social media.

**Recommendation:** Add Open Graph tags (og:title, og:description, og:image, og:url, og:type) and Twitter Card tags (twitter:card, twitter:title, twitter:description, twitter:image) to every page. Use images sized at least 1200x630px for OG and 800x418px for Twitter. Unique tags per page — not the same site-wide defaults.

**Why it matters:** When pages are shared on social media, messaging apps, or Slack, the OG and Twitter Card tags determine how the link preview appears. Missing or poorly configured tags result in broken previews, no images, or generic descriptions — reducing click-through rates from social sharing. These tags also influence how content appears in some search features.

**Key stat:** Content with properly formatted link previews receives 2-3x more engagement when shared on social platforms.

**Source:** Open Graph Protocol. ogp.me — specification documentation (2024). Also: Twitter Developer Documentation. "Cards" — developer.twitter.com (2024). Supplemented by: Moz. "The Ultimate Guide to Open Graph Tags" (2023).

**PASS criteria:**
- og:title, og:description, og:image present on key pages
- Twitter Card tags present (at minimum twitter:card and twitter:title)
- OG images are properly sized (minimum 1200x630px)
- Tags are unique per page, not site-wide defaults on content pages

**FAIL criteria:**
- Missing Open Graph tags entirely
- Missing og:image or using a broken/tiny image
- Same OG title and description across all pages
- No Twitter Card tags present
