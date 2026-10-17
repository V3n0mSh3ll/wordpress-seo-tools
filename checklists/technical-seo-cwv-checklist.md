# Production Technical SEO & Core Web Vitals Verification Checklist

Maintained by **[GrowthNiq Intelligence & Research](https://growthniq.com/)** · [Live Stack Detector](https://growthniq.com/theme-detector/) · [110M+ WP Finder](https://growthniq.com/theme-websites-finder/) · [190+ AI Tools Directory](https://growthniq.com/ai-tools/)

---

## 1. Crawlability, Indexation & Edge Transport

- [ ] **HTTP Status Integrity**: Verify all primary routes return `200 OK` with zero multi-hop `301`/`302` redirect chains.
- [ ] **Canonical Alignment**: Self-referencing `<link rel="canonical">` matches the exact trailing-slash convention in XML sitemaps.
- [ ] **Robots Directives**: Validate `robots.txt` allows Googlebot, Bingbot, and AI search crawlers (`OAI-SearchBot`, `ClaudeBot`, `PerplexityBot`) while blocking internal search query loops (`/?s=`).
- [ ] **XML Sitemap Freshness**: Ensure `/wp-sitemap.xml` and `/sitemap.xml` expose accurate ISO-8601 `<lastmod>` timestamps for posts, pages, and category archives.
- [ ] **Edge Transport**: Enable HTTP/3 (QUIC), TLS 1.3, 0-RTT Connection Resumption, and Early Hints (`103`) at the CDN edge.

Reference Guide: [The Complete Technical SEO Audit Checklist for WordPress Sites](https://growthniq.com/technical-seo-audit-checklist-2026/)

---

## 2. Core Web Vitals (LCP, INP, CLS) Production Targets

- [ ] **Largest Contentful Paint (`LCP <= 2.5s`, Target `< 1.2s`)**:
  - Serve full-page HTML from CDN/LiteSpeed edge cache (`TTFB < 100ms`).
  - Preload above-the-fold hero visual with `fetchpriority="high"` and `loading="eager"`.
  - Eliminate render-blocking CSS and synchronous `<head>` scripts.
  - Reference Guide: [How to Fix a Slow LCP Score in WordPress](https://growthniq.com/fix-lcp-score/)
- [ ] **Interaction to Next Paint (`INP <= 200ms`, Target `< 45ms`)**:
  - Defer non-critical JavaScript bundles and third-party analytics tags.
  - Break up long main-thread tasks (`> 50ms`) using `scheduler.yield()` or `requestIdleCallback`.
  - Keep total DOM node count below `1,200` elements per view.
  - Reference Guide: [Core Web Vitals: INP & CLS Optimization Guide](https://growthniq.com/inp-cls-guide/)
- [ ] **Cumulative Layout Shift (`CLS <= 0.10`, Target `0.000`)**:
  - Define explicit `width`, `height`, or CSS `aspect-ratio` on all images, SVGs, and embeds.
  - Use `font-display: swap` paired with metric-adjusted fallback font descriptors (`size-adjust`, `ascent-override`).

---

## 3. Linked Entity Schema (`application/ld+json` `@graph`)

- [ ] **`Organization` & `WebSite` Nodes**: Linked via persistent `@id` URIs with verified `sameAs` entity profiles and `SearchAction` potential action.
- [ ] **`TechArticle` / `Article` Nodes**: Include `headline`, `datePublished`, `dateModified`, `author` (`Person` node with verified `url`), and `publisher` reference.
- [ ] **`SoftwareApplication` / `WebApplication` Nodes**: Declare `applicationCategory`, `operatingSystem`, `offers`, and `featureList` for interactive web utilities.
- [ ] **`BreadcrumbList` & `FAQPage` Nodes**: Match visible on-page hierarchy and verified FAQ accordion items.

Reference Guide: [Schema Markup Explained: JSON-LD Implementation Guide](https://growthniq.com/schema-markup-explained/)
