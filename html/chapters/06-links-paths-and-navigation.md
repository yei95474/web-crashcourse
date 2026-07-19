# Chapter 6: Links, Paths, and Navigation

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Text Content and Semantics](05-text-content-and-semantics.md) | [Next: Lists and Content Grouping](07-lists-and-content-grouping.md)

## Prerequisites

- Chapters 1-5
- A project containing at least one HTML page

## Learning objectives

You will learn to:

- Create useful hyperlinks with descriptive text.
- Distinguish absolute URLs, root-relative paths, and relative paths.
- Recognize reserved characters and encoded URLs.
- Navigate through nested directories with `../`.
- Link to page fragments, email addresses, telephone numbers, and downloads.
- Create consistent, accessible navigation.
- Use new-tab links safely and sparingly.

## Suggested study time

- Reading and path tracing: 45-60 minutes
- Practice and guided lab: 45-60 minutes

## Key vocabulary

- **Hyperlink**: a connection from one resource or location to another.
- **Absolute URL**: a complete URL containing a scheme and host.
- **Relative path**: a destination calculated from the current document's directory.
- **Root-relative path**: a path beginning at a website's URL root.
- **Fragment**: a named location within a document, introduced by `#` in a URL.
- **Percent encoding**: URL notation that represents characters with percent-prefixed byte values.
- **Breadcrumb**: navigation showing the current page's position in a hierarchy.
- **Link relationship**: metadata describing how the current and linked resources are related.

## 6.1 Links make the Web a web

The anchor element connects a source to a destination:

```html
<a href="about.html">Read about our club</a>
```

`a` means anchor. `href` means hypertext reference. The content is the link's visible and accessible name.

Write link text that describes the destination. “Read the registration guide” is more useful than “click here,” especially when a screen-reader user lists links without surrounding paragraphs.

## 6.2 Absolute URLs

An **absolute URL** includes the scheme and host:

```html
<a href="https://developer.mozilla.org/">Visit MDN Web Docs</a>
```

Use an absolute URL when linking to a resource on another website. If its domain or path changes, your link can break; test external links periodically.

## 6.3 Relative paths

A **relative path** gives directions starting from the current document.

```text
club-site/
  index.html
  about.html
  pages/
    events.html
  images/
    logo.png
```

From `index.html`:

```html
<a href="about.html">About</a>
<a href="pages/events.html">Events</a>
<img src="images/logo.png" alt="Club logo">
```

From `pages/events.html`, move up to the project root with `..`:

```html
<a href="../index.html">Home</a>
<img src="../images/logo.png" alt="Club logo">
```

`.` means the current directory; `..` means the parent directory. Do not write a Windows filesystem path such as `C:\Users\Name\site\about.html` in a website. It points to your computer, not a portable project location.

A path beginning with `/`, such as `/images/logo.png`, is **root-relative** to a website's origin. This can be useful when hosted but often fails when opening local files directly. Course projects favor document-relative paths.

## URL encoding and reserved characters

URLs use characters such as `/`, `?`, `#`, `&`, and `=` as syntax. Other characters may be represented with **percent encoding**. A space commonly appears as `%20`:

```text
course%20notes.pdf
```

Avoid spaces in project filenames so humans do not need to reason about encoded versions.

Inside HTML source, an ampersand beginning another query parameter should be written as `&amp;`:

```html
<a href="search.html?q=html&amp;level=beginner">
  Beginner HTML search
</a>
```

The browser interprets the character reference as `&` in the URL. Do not manually percent-encode an entire URL without understanding which characters are syntax and which are data. URL encoding and HTML character references solve related but different problems.

## 6.4 Directory index pages

Web servers commonly treat `index.html` as the default file for a directory. A link to `products/` may serve `products/index.html`. Locally, behavior can vary, so writing explicit filenames during early practice is clearer.

## 6.5 Fragment links

An `id` identifies one element in a document:

```html
<h2 id="requirements">Requirements</h2>
```

Link to it with a fragment:

```html
<a href="#requirements">Jump to requirements</a>
```

From another page:

```html
<a href="course.html#requirements">Course requirements</a>
```

IDs must be unique within a document. Use short, meaningful, stable values. The browser scrolls the target into view, and the URL gains the fragment.

## 6.6 Email, telephone, and download links

```html
<a href="mailto:help@example.com">Email the help desk</a>
<a href="tel:+6325550123">Call +63 2 555 0123</a>
<a href="files/guide.pdf" download>Download the course guide (PDF)</a>
```

These links request an appropriate application or download behavior; they do not guarantee what a device will do. Display useful contact information so users can copy it.

Do not prefill sensitive information in a `mailto` URL. Email links also expose addresses to page readers and automated tools.

## 6.7 Same tab or new tab?

Normal links should usually use the current tab. Users know how to open a new one when desired. If a strong reason requires a new tab:

```html
<a href="https://example.com"
   target="_blank"
   rel="noopener">
  Open the external reference in a new tab
</a>
```

Warn users in the link text when the behavior may surprise them. `rel="noopener"` prevents the opened page from receiving a direct reference to the opener in older or unusual contexts.

`rel` can describe other relationships, such as `author`, `help`, `license`, `prev`, `next`, `external`, or `noreferrer`. Use a token only when the relationship is true. These values describe relationships; most do not automatically change visible presentation.

## 6.8 Navigation landmarks

Group a major navigation set in `nav`:

```html
<nav aria-label="Primary">
  <a href="index.html">Home</a>
  <a href="about.html">About</a>
  <a href="contact.html">Contact</a>
</nav>
```

`nav` is for major navigation, not every cluster of links. When a page has several navigation regions, labels distinguish them. Chapter 7 will improve this example with a list.

Keep navigation order, wording, and destinations consistent on every page. Marking the current page can help:

```html
<a href="about.html" aria-current="page">About</a>
```

## Breadcrumb navigation

A breadcrumb shows the current page's place in a hierarchy:

```html
<nav aria-label="Breadcrumb">
  <ol>
    <li><a href="../index.html">Home</a></li>
    <li><a href="courses.html">Courses</a></li>
    <li><span aria-current="page">HTML</span></li>
  </ol>
</nav>
```

Use an ordered list because the sequence from broad to specific matters. The current item need not link to itself. Breadcrumbs supplement rather than replace primary navigation and a clear page heading.

## 6.9 Practice

**C06-Q1 - Fill in the blanks.**

```html
<a ____="about.html">_____ us</a>
```

Complete a link whose text is “About us.”

**C06-Q2 - Path puzzle.** From `pages/contact.html`, write the relative path to `images/map.png`:

```text
site/
  pages/
    contact.html
  images/
    map.png
```

**C06-Q3 - Semantic choice.** Which link text is better: “click here” or “download the laboratory rules (PDF)”? Why?

**C06-Q4 - Fragment puzzle.** Write a heading with ID `fees` and a link that jumps to it.

**C06-Q5 - Spot the bug.** Why will this path fail for other users?

```html
<a href="C:\Users\Mina\site\about.html">About</a>
```

**C06-Q6 - Core challenge.** Add three-page navigation and mark `contact.html` as the current page on that page.

**C06-Q7 - Pause and predict.** From `index.html`, what does `pages/../about.html` resolve to? Is the simpler path preferable?

**C06-Q8 - Encoding puzzle.** Why should this source use `&amp;` rather than a literal `&`?

```html
<a href="results.html?topic=html&amp;level=1">Results</a>
```

## Guided lab: three connected pages

Create:

```text
projects/about-me/
  index.html
  about.html
  contact.html
```

Add identical primary navigation to all pages. Give every page a unique `title` and `h1`. Use `aria-current="page"` on the current navigation item. Test all nine navigation links, not only links from the homepage.

Add a “Skip to main content” fragment link at the start of one page:

```html
<a href="#main-content">Skip to main content</a>
<main id="main-content">
  ...
</main>
```

It will become more useful after CSS controls its presentation, but its destination should work now.

## Stretch challenge: compute paths without guessing

Draw a directory tree with two nested page folders and one shared image folder. For each HTML file, calculate the path to every other page and the image. Then create the files and test your calculations.

When a path fails, do not add random `../` segments. State the starting file, trace to the common ancestor, then trace down to the target.

## Common misconceptions

- Link text is not just decoration; it names the destination.
- A relative path starts from the current file's directory.
- A leading slash does not mean “project folder” when opening local files.
- An `id` must be unique.
- New tabs are not automatically more professional.
- `mailto:` submits no web form; it asks the user's email software to act.

## Chapter summary

Anchors connect documents and locations. Absolute URLs identify external resources; relative paths navigate a project from the current file. Fragments use unique IDs. Descriptive link text, predictable tab behavior, and consistent navigation make links understandable and accessible.

## Mastery checklist

- [ ] I can create descriptive links.
- [ ] I can compute relative paths using a directory tree.
- [ ] I can create and target fragments.
- [ ] I understand email, telephone, and download links.
- [ ] I use new-tab behavior only deliberately.
- [ ] I can build consistent multi-page navigation.
- [ ] I can distinguish URL encoding from HTML character references.
- [ ] I can mark a breadcrumb as ordered navigation.

Solutions: [Content and navigation answer key](../answer-keys/02-content-and-navigation.md#chapter-6)

## Authoritative references

- [WHATWG: URLs](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#urls)
- [WHATWG: Links](https://html.spec.whatwg.org/multipage/links.html)
- [W3C WAI: Menus and navigation](https://www.w3.org/WAI/tutorials/menus/)

[Next: Chapter 7 - Lists and Content Grouping](07-lists-and-content-grouping.md)
