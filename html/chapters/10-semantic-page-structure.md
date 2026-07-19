# Chapter 10: Semantic Page Structure

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Audio, Video, and Embedded Content](09-audio-video-and-embedded-content.md) | [Next: Tables and Structured Data](11-tables-and-structured-data.md)

## Prerequisites

- Chapters 1-9
- Heading hierarchy, links, lists, and tree relationships

## Learning objectives

You will learn to:

- Identify major page regions with semantic elements.
- Choose among `main`, `article`, `section`, `aside`, `header`, and `footer`.
- Build useful landmarks and a logical heading outline.
- Identify a search or filtering region with the `search` element.
- Distinguish document structure from visual layout.
- Plan a page before writing markup.

## Suggested study time

- Reading and structural analysis: 45-60 minutes
- Practice and guided lab: 45-65 minutes

## Key vocabulary

- **Landmark**: a major page region that assistive technology can navigate.
- **Main content**: the central content unique to the current document.
- **Article**: a self-contained composition that can stand independently.
- **Section**: a thematic grouping that normally has a heading.
- **Aside**: content indirectly related to nearby or surrounding content.
- **Navigation region**: a major collection of links for moving through content.
- **Search region**: controls used to search or filter a site or collection.
- **Document outline**: the hierarchy communicated by headings and sections.

## 10.1 Structure serves navigation and understanding

Sighted readers may infer page regions from columns, colors, and spacing. Software needs explicit meaning. Semantic structural elements create recognizable regions and help developers understand a document.

A common skeleton:

```html
<body>
  <header>
    <p>Community Science Club</p>
  </header>

  <nav aria-label="Primary">
    <ul>
      <li><a href="index.html">Home</a></li>
      <li><a href="events.html">Events</a></li>
    </ul>
  </nav>

  <main>
    <h1>Upcoming Events</h1>
    <p>Join our monthly workshops.</p>
  </main>

  <footer>
    <p>&copy; 2026 Community Science Club</p>
  </footer>
</body>
```

This is semantic architecture, not a visual design. CSS later decides whether navigation is horizontal and where the footer appears.

## 10.2 Major elements

### `main`

`main` contains content unique to the page's central purpose. A typical document has one visible `main`. Repeated site navigation, logos, and legal footer content generally sit outside it.

### `nav`

`nav` contains a major set of navigation links. A page may have primary, breadcrumb, table-of-contents, and footer navigation. Label multiple regions so users can distinguish them.

### `header`

`header` introduces a page or section. A body-level header may contain site identity and navigation. An article header may contain its title, author, and date. It is not defined as “the top strip.”

### `footer`

`footer` provides information about its nearest sectioning content or the page: author, related links, copyright, or contact information. It is not defined merely by bottom placement.

### `article`

`article` encloses content that is independently reusable or distributable, such as a news story, forum post, product card, or blog entry.

```html
<article>
  <header>
    <h2>Robotics Team Wins Regional Final</h2>
    <p>Published <time datetime="2026-07-14">July 14, 2026</time></p>
  </header>
  <p>The team completed all three challenges...</p>
</article>
```

### `section`

`section` groups a thematic part of a document and normally has a heading:

```html
<section>
  <h2>Registration Requirements</h2>
  <p>Participants must be at least 16 years old.</p>
</section>
```

Do not use `section` as a generic styling wrapper. If you cannot name the section, a `div` may be more honest—or no wrapper may be needed.

### `aside`

`aside` contains content indirectly related to surrounding content: a glossary box, related links, author biography, or contextual note. It does not automatically mean a visual sidebar.

### `search`

`search` contains controls or content for searching or filtering:

```html
<search>
  <form action="/search" method="get">
    <label for="site-search">Search course articles</label>
    <input
      id="site-search"
      name="q"
      type="search">
    <button type="submit">Search</button>
  </form>
</search>
```

Use it for an actual search or filtering feature, not every form containing an input of type `search`. The element can expose a search landmark without adding `role="search"`.

`search` is newer than the long-established structural elements. Verify the browsers and assistive technologies required by a production project; a properly labeled form remains understandable even when the extra landmark is not exposed.

## 10.3 `article` versus `section`

Ask:

- Could this piece reasonably stand alone in a feed, search result, or syndication? Consider `article`.
- Is it a thematic subdivision of a larger document? Consider `section`.
- Is it only needed for styling or scripting? Consider `div`.

Elements can nest:

```html
<article>
  <h1>Beginner Gardening</h1>
  <section>
    <h2>Choosing soil</h2>
    ...
  </section>
  <section>
    <h2>Watering</h2>
    ...
  </section>
</article>
```

Context determines meaning; no keyword can decide every case.

## 10.4 Landmarks and headings cooperate

Elements such as `header`, `nav`, `main`, `aside`, and `footer` can expose **landmarks** that assistive-technology users navigate. Headings provide a second navigation system through content.

Do not put headings into every landmark mechanically. A primary `nav` can be labeled with `aria-label`. Sections and articles normally benefit from headings because their topic must be understandable.

Use native semantic elements before adding ARIA roles:

```html
<nav>...</nav>
```

is clearer than:

```html
<div role="navigation">...</div>
```

## 10.5 Plan before markup

Start with content, not boxes. For an event page, a content inventory might be:

- Site name
- Primary navigation
- Event title and summary
- Date and location
- Schedule
- Registration requirements
- Related events
- Contact and copyright

Then assign meaning:

```text
header
nav
main
  article
    header
    section: schedule
    section: requirements
  aside: related events
footer
```

Finally write HTML. This sequence avoids choosing elements because of an imagined visual layout.

## 10.6 Practice

**C10-Q1 - Semantic choice.** Which element should contain content unique to the page's central purpose?

**C10-Q2 - Semantic choice.** Choose `article`, `section`, or `div` for a complete news story that could appear in a feed.

**C10-Q3 - Spot the misconception.** Correct: “An `aside` must appear on the right side of the screen.”

**C10-Q4 - Fill in the blanks.**

```html
<____>
  <h1>Course Catalog</h1>
  <section>...</section>
</____>
```

Use the element for unique central content.

**C10-Q5 - Tree reasoning.** Can an `article` contain sections? Can a section contain articles? Explain with context.

**C10-Q6 - Core challenge.** Assign semantic elements to a site name, primary links, unique article, related-links box, and copyright notice.

**C10-Q7 - Accessibility choice.** Which is preferred for primary navigation: `nav` or `div role="navigation"`?

**C10-Q8 - Semantic choice.** Which element should wrap a form whose purpose is filtering the site's article catalog, and should it also receive `role="search"`?

## Guided lab: refactor the recipe

Revise the recipe site:

1. Put site identity in a body-level `header`.
2. Put major links in `nav`.
3. Put the recipe's unique content in `main`.
4. Decide whether the recipe is an `article`.
5. Group ingredients and procedure into headed `section` elements.
6. Put substitutions in an `aside` only if they are supplementary.
7. Add a body-level `footer`.
8. Review the heading hierarchy independently of appearance.

## Stretch challenge: semantic debate

For a page showing ten independent product reviews, decide whether the page should use:

- One `article` containing ten `section` elements,
- Ten `article` elements inside `main`, or
- Generic containers.

Defend your decision based on whether each review stands independently. Identify a scenario where a different option would become reasonable.

## Checkpoint 2

Create a two-page site from a blank folder without consulting chapter examples. It must use:

- Valid document skeletons.
- Unique titles and main headings.
- Relative navigation.
- A list.
- An informative image with suitable alt text.
- Meaningful page regions.

Test every link and inspect both document trees. Use the [small-site rubric](../reference/project-rubrics.md#project-2-recipe-or-hobby-site) for feedback.

## Common misconceptions

- Semantic elements do not determine screen position.
- `header` and `footer` may belong to a page or a section.
- `section` is not a replacement for every `div`.
- `article` means independently meaningful content, not merely “contains words.”
- A good heading outline and landmarks solve related but distinct navigation needs.

## Chapter summary

Semantic page elements describe regions by purpose. `main` identifies unique central content, `nav` major navigation, `article` self-contained material, `section` a thematic subdivision, and `aside` supplementary content. Headers and footers belong to their nearest relevant scope. Plan content relationships before visual layout.

## Mastery checklist

- [ ] I can identify the main landmarks of a page.
- [ ] I choose `article`, `section`, and `div` by meaning.
- [ ] I understand that semantics do not determine placement.
- [ ] I can plan a page as a content tree.
- [ ] I use native elements before equivalent ARIA roles.
- [ ] My headings make the structure understandable.
- [ ] I can identify a genuine search or filtering region.

Solutions: [Media, structure, and tables answer key](../answer-keys/03-media-structure-and-tables.md#chapter-10)

## Authoritative references

- [WHATWG: Sections](https://html.spec.whatwg.org/multipage/sections.html)
- [WHATWG: The search element](https://html.spec.whatwg.org/multipage/grouping-content.html#the-search-element)
- [W3C WAI: Page structure](https://www.w3.org/WAI/tutorials/page-structure/)

[Next: Chapter 11 - Tables and Structured Data](11-tables-and-structured-data.md)
