# Chapter 14: The Document Head and Metadata

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Validation and Form Submission](13-validation-and-form-submission.md) | [Next: Accessible HTML](15-accessible-html.md)

## Prerequisites

- Chapters 1-13
- The basic document skeleton

## Learning objectives

You will learn to:

- Write unique, descriptive page titles and descriptions.
- Explain charset and viewport metadata.
- Link icons, stylesheets, and scripts.
- Understand canonical and social-sharing metadata at an introductory level.
- Recognize robots directives, manifests, resource hints, structured data, and `base`.
- Distinguish metadata from visible content.
- Audit the head of every page in a site.
- Identify separately published alternate-language documents.

## Suggested study time

- Reading and metadata comparison: 45-55 minutes
- Practice and guided lab: 40-55 minutes

## Key vocabulary

- **Metadata**: information that describes, configures, or relates a document.
- **Page title**: the document name used by tabs, bookmarks, history, and other tools.
- **Meta description**: a concise description that some services may use when presenting a page.
- **Favicon**: a small icon associated with a site or page.
- **Canonical URL**: the preferred URL for substantially equivalent versions of content.
- **Resource hint**: metadata suggesting that the browser prepare for a likely resource operation.
- **Manifest**: linked metadata that describes an installable web application's identity and presentation.
- **Structured data**: machine-readable information about entities and relationships in page content.

## 14.1 The head is part of the user experience

Head content is usually not displayed in the document body, but it affects tabs, bookmarks, history, search previews, mobile behavior, icons, styling, and scripting.

A practical starting point:

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta
    name="description"
    content="Beginner-friendly notes and exercises for learning semantic HTML.">
  <title>HTML Study Notes | Mina's Portfolio</title>
  <link rel="icon" href="images/favicon.ico">
</head>
```

Place the charset declaration early in `head` so the browser identifies encoding promptly.

## 14.2 Page titles

Every page needs a concise, unique `title` that identifies both page and site:

```html
<title>Registration | Community Science Club</title>
```

Poor titles:

- `Home`
- `Untitled Document`
- The same `Community Science Club` on every page
- A long list of keywords

A title should make sense in a crowded row of tabs and in browser history. The specific page topic commonly comes before the site name.

The visible `h1` and document `title` can be similar but solve different interface needs.

## 14.3 Meta descriptions

```html
<meta
  name="description"
  content="Register for free community science workshops in August.">
```

A meta description summarizes the page. Search engines may choose it as a result snippet, but they may also select different text. It does not replace clear visible content and does not guarantee ranking.

Write a truthful, page-specific sentence. Avoid keyword stuffing.

The old `meta name="keywords"` field is not a meaningful modern SEO strategy and is omitted from this course.

## 14.4 Viewport and mobile pages

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This instructs mobile browsers to use the device width as the layout viewport and begin at normal scale. It does not create a responsive design on its own, but it allows later responsive CSS to behave as intended.

Do not disable user zoom with values such as `user-scalable=no`; zoom is an important accessibility feature.

## 14.5 Favicons

```html
<link rel="icon" href="images/favicon.svg" type="image/svg+xml">
```

Favicons identify a site in tabs, bookmarks, and shortcuts. Browser and device conventions vary, so production sites may provide multiple icon sizes and a web app manifest. One valid icon is enough for this HTML course.

## 14.6 Linking CSS and JavaScript

External CSS:

```html
<link rel="stylesheet" href="styles/site.css">
```

External JavaScript:

```html
<script src="scripts/site.js" defer></script>
```

`defer` tells a classic external script to execute after document parsing while preserving order among deferred scripts. Module scripts have different default behavior:

```html
<script type="module" src="scripts/app.js"></script>
```

You will not write CSS or JavaScript in this book, but you should recognize how documents connect to them. Broken paths affect supporting files exactly as they affect links and images.

## 14.7 Canonical URLs

When equivalent content is reachable through several URLs, a production site can suggest a preferred URL:

```html
<link rel="canonical" href="https://example.org/courses/html">
```

Use an absolute public URL and only when you control the publishing decision. A canonical link is not useful in an unpublished local exercise and does not redirect visitors.

## 14.8 Social-sharing metadata

Platforms may read Open Graph-style properties:

```html
<meta property="og:title" content="HTML Study Notes">
<meta property="og:description" content="A beginner's guide to semantic HTML.">
<meta property="og:image" content="https://example.org/images/share-card.jpg">
<meta property="og:url" content="https://example.org/html-notes">
```

These are ecosystem conventions rather than core substitutes for `title`, descriptions, or visible content. Public absolute URLs are generally necessary. Requirements change, so verify current platform documentation before publishing.

### Alternate-language documents

When separately published pages provide equivalent content in different languages, `link` metadata can describe the alternatives:

```html
<link
  rel="alternate"
  hreflang="en"
  href="https://example.org/en/course">
<link
  rel="alternate"
  hreflang="fil"
  href="https://example.org/fil/kurso">
```

`hreflang` describes the linked document's language; it does not translate content or choose a language for the visitor. Each document still needs an accurate root `lang`, working reciprocal navigation, and a publishing strategy.

## 14.9 Robots directives

A robots meta directive can communicate indexing preferences:

```html
<meta name="robots" content="noindex, nofollow">
```

Search crawlers may interpret tokens such as `index`, `noindex`, `follow`, or `nofollow` according to their policies. This is not access control. A page carrying `noindex` can still be requested, shared, logged, or discovered. Private information needs authentication and server protection.

## 14.10 Manifests and structured data

A web app manifest is linked from the head:

```html
<link rel="manifest" href="site.webmanifest">
```

It supplies application metadata such as names and icons, but does not by itself make a site installable or offline-capable.

Structured data can describe visible entities such as events or organizations for machine consumers. Common approaches include HTML microdata and JSON-LD. The data must agree with truthful visible content and does not guarantee special search presentation.

Both are recognition topics in [Appendix 2](../appendices/02-less-common-html-and-platform-boundaries.md).

## 14.11 Resource hints

`preload` can request an important resource early:

```html
<link
  rel="preload"
  href="fonts/course-heading.woff2"
  as="font"
  type="font/woff2"
  crossorigin>
```

`preconnect` can prepare a connection to a known origin:

```html
<link rel="preconnect" href="https://static.example.org">
```

Hints can waste bandwidth or connections when overused. Add them after measurement, supply correct attributes, and confirm that the hinted resource is actually used.

## 14.12 The `base` warning

`base` can change how every relative URL in a document resolves:

```html
<base href="https://example.org/courses/html/">
```

It affects links, images, forms, scripts, stylesheets, and fragments—not just one section. Most course projects should avoid it and use explicit relative paths. Learn it to diagnose existing pages; see [Appendix 2](../appendices/02-less-common-html-and-platform-boundaries.md#a21-the-base-element).

## 14.13 SEO begins with meaningful content

Search discoverability is supported by:

- Unique, descriptive titles.
- Accurate headings and visible text.
- Meaningful links.
- Useful image alternatives.
- Fast, mobile-friendly pages.
- Logical information architecture.
- Pages that answer real user needs.

Metadata cannot rescue empty, misleading, inaccessible, or duplicated content.

## 14.14 Practice

**C14-Q1 - Warm-up.** Where does `title` normally appear to the user?

**C14-Q2 - Rewrite.** Improve `<title>Page 2</title>` for the contact page of “Green Garden Club.”

**C14-Q3 - Fill in the blanks.**

```html
<meta name="________" content="width=device-width, initial-scale=1.0">
```

**C14-Q4 - Pause and predict.** Does a meta description guarantee that exact text appears in a search result?

**C14-Q5 - Accessibility reasoning.** Why should a page not disable zoom?

**C14-Q6 - Path puzzle.** From `pages/about.html`, link a stylesheet at `styles/site.css` in the project root.

**C14-Q7 - Core challenge.** Write a useful head for a local “Event Registration” page, including charset, viewport, description, and title.

**C14-Q8 - Concept check.** Does a canonical link redirect a user? What does it communicate?

**C14-Q9 - Security misconception.** Does `<meta name="robots" content="noindex">` make a page private? Explain the correct boundary.

## Guided lab: head audit

Audit every page in your event project:

1. Confirm one UTF-8 declaration.
2. Confirm the standard viewport setting.
3. Write a unique title with page and site identity.
4. Write a truthful page-specific description.
5. Verify any icon or future stylesheet path from that page's location.
6. Compare open browser tabs: can you distinguish the pages by title?

## Stretch challenge: search-result editor

Write title and description pairs for:

- A homepage.
- An event details page.
- A contact page.

Keep each pair specific without repeating the same opening phrase. Then inspect whether the visible `h1` still honestly matches the page.

## Common misconceptions

- Head metadata can affect interfaces even when it is not body content.
- `title` and `h1` are not interchangeable.
- Meta descriptions are suggestions, not guaranteed search snippets.
- The viewport tag enables proper scaling; it does not supply layout.
- Canonical metadata is not a redirect.
- Social metadata supplements rather than replaces standards-based metadata.

## Chapter summary

The document head identifies, describes, configures, and connects a page. Unique titles and accurate descriptions improve orientation and discoverability. Charset and viewport metadata support correct text and mobile behavior. Links connect icons, stylesheets, scripts, and publishing hints.

## Mastery checklist

- [ ] Every page has a useful, unique title.
- [ ] I can write an honest meta description.
- [ ] I understand charset and viewport metadata.
- [ ] I can compute head-resource paths.
- [ ] I distinguish canonical, favicon, stylesheet, and script links.
- [ ] I understand metadata's limits.
- [ ] I recognize robots, manifest, resource-hint, structured-data, and base metadata without treating them as magic.
- [ ] I can identify separately published language alternatives without confusing `hreflang` with `lang`.

Solutions: [Forms and accessibility answer key](../answer-keys/04-forms-and-accessibility.md#chapter-14)

## Authoritative references

- [WHATWG: Document metadata](https://html.spec.whatwg.org/multipage/semantics.html#document-metadata)
- [WHATWG: Link types](https://html.spec.whatwg.org/multipage/links.html#linkTypes)
- [WHATWG: The base element](https://html.spec.whatwg.org/multipage/semantics.html#the-base-element)

[Next: Chapter 15 - Accessible HTML](15-accessible-html.md)
