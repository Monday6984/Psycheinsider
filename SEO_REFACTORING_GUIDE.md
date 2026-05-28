# PsycheInsider Website Refactoring Guide

## Overview

This document outlines the complete refactoring of your website from HTML-based routing to clean URLs with comprehensive SEO improvements.

---

## 1. URL STRUCTURE CHANGES

### Before (HTML-based):

```
/index.html       → /index.html
/about.html       → /about.html
/services.html    → /services.html
/contact.html     → /contact.html
/optimize.html    → /optimize.html
```

### After (Clean URLs):

```
/                 → Homepage (index.html)
/about            → About page (about.html)
/services         → Services page (services.html)
/contact          → Contact page (contact.html)
/optimize         → Optimize page (optimize.html)
/blog             → Blog (future page)
```

---

## 2. IMPLEMENTATION STEPS

### Step 1: `.htaccess` Configuration ✅ DONE

- Removes `.html` extension from URLs
- Redirects old `.html` URLs to clean URLs (301 permanent)
- Enables compression & caching
- Adds security headers
- Forces HTTPS (optional)

### Step 2: Update All HTML Navigation

**All 5 files need navigation updates:**

```html
<!-- CORRECT NAVIGATION -->
<a href="/">Home</a>
<a href="/about">About</a>
<a href="/optimize">OPTIMIZE</a>
<a href="/blog">Blog</a>
<a href="/services">Services</a>
<a href="/contact">Contact</a>
```

### Step 3: Add SEO Meta Tags

Every page needs these in the `<head>`:

```html
<!-- Essential Meta Tags -->
<meta name="description" content="[Page-specific description 155-160 chars]" />
<meta name="keywords" content="[Relevant keywords]" />
<meta name="author" content="PsycheInsider" />
<meta name="language" content="English" />

<!-- Canonical URL (CRITICAL for clean URLs) -->
<link rel="canonical" href="https://psycheinsider.com[/page-path]" />

<!-- Open Graph (Social Sharing) -->
<meta property="og:type" content="website" />
<meta property="og:title" content="[Page Title]" />
<meta property="og:description" content="[Page description]" />
<meta property="og:image" content="https://psycheinsider.com/[image-path]" />
<meta property="og:url" content="https://psycheinsider.com[/page-path]" />

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="[Page Title]" />
<meta name="twitter:description" content="[Page description]" />
<meta name="twitter:image" content="https://psycheinsider.com/[image-path]" />
```

### Step 4: Add Internal Links & Fix Active States

- Remove hardcoded active states (check current page dynamically)
- Update all `href="#"` to proper URLs
- Add footer contact link: `<a href="/contact">`

### Step 5: Image Alt Text & Accessibility

Every image needs meaningful alt text:

```html
<!-- WRONG -->
<img src="" alt="" aria-hidden="true" />
<img src="" alt="" />

<!-- CORRECT -->
<img src="/images/founder.jpg" alt="PsycheInsider Founder Portrait" />
<img src="/images/team.jpg" alt="PsycheInsider Team" />
```

### Step 6: Heading Structure

- H1: Page main title (1 per page)
- H2: Section titles
- H3: Subsection titles
- No skipped levels (H1 → H3 is wrong)

---

## 3. PAGE-SPECIFIC SEO METADATA

### Homepage (index.html)

**URL:** `/` (root)
**Title:** `PsycheInsider - Professional Psychology Services & Personal Optimization`
**Meta Description:** `Evidence-based psychology services and personal optimization programs. Book consultations, explore OPTIMIZE, or partner with us today.`
**Canonical:** `https://psycheinsider.com/`

### About Page (about.html)

**URL:** `/about`
**Title:** `About PsycheInsider - Our Mission & Approach`
**Meta Description:** `Learn about PsycheInsider's mission, founder, and our evidence-based approach to psychology and personal development.`
**Canonical:** `https://psycheinsider.com/about`

### Services Page (services.html)

**URL:** `/services`
**Title:** `Professional Psychology Services - Individual & Corporate`
**Meta Description:** `Explore our psychology consultation services, from individual therapy to corporate wellness programs. Book your consultation today.`
**Canonical:** `https://psycheinsider.com/services`

### Contact Page (contact.html)

**URL:** `/contact`
**Title:** `Contact PsycheInsider - Get In Touch`
**Meta Description:** `Get in touch with PsycheInsider for consultations, partnerships, or media inquiries. We respond within 48 hours.`
**Canonical:** `https://psycheinsider.com/contact`

### Optimize Page (optimize.html)

**URL:** `/optimize`
**Title:** `OPTIMIZE - Advanced Psychology Personal Development Program`
**Meta Description:** `Discover OPTIMIZE, our comprehensive personal development program combining psychology, neuroscience, and behavioral optimization.`
**Canonical:** `https://psycheinsider.com/optimize`

---

## 4. DUPLICATE URL PREVENTION

### ✅ DO:

- Use one canonical URL per page
- Redirect old URLs (301 permanent)
- Consistent internal linking
- No URL parameters for navigation

### ❌ DON'T:

- Serve pages at both `/about` and `/about.html`
- Use different link formats on different pages
- Link to www vs non-www versions
- Use session IDs or tracking parameters in canonical URLs

---

## 5. INTERNAL LINKING STRATEGY

### Homepage Links:

- "Learn About Us" → `/about`
- "Explore Services" → `/services`
- "Book OPTIMIZE" → `/optimize`
- "Contact Us" → `/contact`

### About Page Links:

- "Our Services" → `/services`
- "Ready to Begin?" → `/contact`
- "Explore OPTIMIZE" → `/optimize`

### Services Page Links:

- "About Our Approach" → `/about`
- "Let's Get Started" → `/contact`
- "Advanced Option" → `/optimize`

### Contact Page Links:

- "Learn More About Us" → `/about`
- "Explore Our Services" → `/services`

### Optimize Page Links:

- "Our Services" → `/services`
- "Enroll Now" → `/contact`

### Footer (All Pages):

```html
<a href="/">Home</a>
<a href="/about">About</a>
<a href="/services">Services</a>
<a href="/optimize">OPTIMIZE</a>
<a href="/blog">Blog</a>
<a href="/contact">Contact</a>
```

---

## 6. IMPLEMENTATION CHECKLIST

### Before Going Live:

- [ ] `.htaccess` file created with rewrite rules
- [ ] All HTML files updated with correct navigation links
- [ ] All meta descriptions added (unique for each page)
- [ ] Canonical URLs set on every page
- [ ] Open Graph tags added
- [ ] Twitter Card tags added
- [ ] All image alt text added
- [ ] Heading structure reviewed
- [ ] Internal links checked (no dead links)
- [ ] Active navigation states updated
- [ ] Footer links updated
- [ ] Contact form action updated if needed

### After Going Live:

- [ ] Test all URLs work (both `/page` and `/page.html`)
- [ ] Check 301 redirects with redirect checker tool
- [ ] Verify canonical tags in Google Search Console
- [ ] Submit new sitemap to Google/Bing
- [ ] Monitor 404 errors
- [ ] Check Google Analytics for traffic

---

## 7. QUICK REFERENCE: URL MAPPINGS

| Page     | Old URL        | New URL   | File          |
| -------- | -------------- | --------- | ------------- |
| Homepage | /index.html    | /         | index.html    |
| About    | /about.html    | /about    | about.html    |
| Services | /services.html | /services | services.html |
| Contact  | /contact.html  | /contact  | contact.html  |
| Optimize | /optimize.html | /optimize | optimize.html |

---

## 8. TESTING URLS

### Local Testing (Before Server Upload):

1. Test htaccess locally if possible
2. Verify links work on uploaded server
3. Test both `/page` and `/page.html` resolve to same content

### After Upload:

Use these tools:

- **Redirect Checker:** redirectdetective.com
- **Link Checker:** w3c.org/checklink
- **Google Search Console:** search.google.com/search-console

---

## 9. PERFORMANCE TIPS

The `.htaccess` also includes:

- **Compression:** Gzip compression enabled
- **Caching:** Browser caching for images (1 year), CSS/JS (1 month)
- **Security Headers:** Protection against common attacks
- **HTTPS:** Force HTTPS (uncomment in .htaccess when ready)

---

## NEXT STEPS

1. Review this guide
2. Verify `.htaccess` is correct for your server
3. Update all HTML files with proper links and meta tags
4. Test all URLs thoroughly
5. Monitor for any 404 errors or issues
6. Update external links if they point to your old URLs
