# Chapter 7: Lists and Content Grouping

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Links, Paths, and Navigation](06-links-paths-and-navigation.md) | [Next: Images, Figures, and Responsive Media](08-images-figures-and-responsive-media.md)

## Prerequisites

- Chapters 1-6
- Basic links and semantic text

## Learning objectives

You will learn to:

- Choose ordered, unordered, or description lists by meaning.
- Nest lists with valid parent-child relationships.
- Mark navigation as a list of links.
- Use `div` and `span` only when no semantic element fits.
- Group related content without creating “container soup.”

## Suggested study time

- Reading and examples: 35-45 minutes
- Practice and guided lab: 35-50 minutes

## Key vocabulary

- **Unordered list**: a collection whose sequence is not essential.
- **Ordered list**: a collection whose sequence or ranking matters.
- **Description list**: associations between names or terms and their descriptions.
- **List item**: one member of an ordered or unordered list.
- **Nested list**: a list placed inside a parent list item.
- **Generic container**: a `div` or `span` used when no more meaningful element fits.
- **Grouping**: marking content as belonging together because of a real relationship.

## 7.1 Lists express relationships

A list says that several items belong together. HTML supplies three major kinds.

### Unordered lists

Use `ul` when sequence is not essential:

```html
<h2>Equipment</h2>
<ul>
  <li>Notebook</li>
  <li>Pencil</li>
  <li>Safety glasses</li>
</ul>
```

Reordering these items does not change the instructions.

### Ordered lists

Use `ol` when order or rank matters:

```html
<h2>Procedure</h2>
<ol>
  <li>Read the instructions.</li>
  <li>Collect the equipment.</li>
  <li>Begin the experiment.</li>
</ol>
```

Switching Steps 1 and 3 would change the procedure.

### Description lists

Use `dl` for name-value groups, terms and definitions, or metadata:

```html
<dl>
  <dt>HTML</dt>
  <dd>A language for structuring web content.</dd>

  <dt>Browser</dt>
  <dd>Software that interprets and presents web resources.</dd>
</dl>
```

`dt` marks a name or term; `dd` provides its description or value. A description list can associate more than one term or description when the content requires it.

## 7.2 Valid nesting

The direct children of `ul` and `ol` are `li` elements. Put a nested list *inside* the list item that owns it:

```html
<ul>
  <li>
    Frontend
    <ul>
      <li>HTML</li>
      <li>CSS</li>
    </ul>
  </li>
  <li>Backend</li>
</ul>
```

Incorrect:

```html
<ul>
  <li>Frontend</li>
  <ul>
    <li>HTML</li>
  </ul>
</ul>
```

Tree reasoning reveals the error: the inner `ul` must be a descendant of an `li`, not its sibling.

## 7.3 Useful ordered-list attributes

Continue numbering from a particular value:

```html
<ol start="4">
  <li>Review the result.</li>
  <li>Submit the report.</li>
</ol>
```

Mark a reversed countdown:

```html
<ol reversed>
  <li>Finalist</li>
  <li>Runner-up</li>
  <li>Winner</li>
</ol>
```

Use these only when numbering carries content meaning. CSS changes marker appearance later.

## 7.4 Navigation as a list

A navigation menu is conceptually a list of destinations:

```html
<nav aria-label="Primary">
  <ul>
    <li><a href="index.html" aria-current="page">Home</a></li>
    <li><a href="about.html">About</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
</nav>
```

The browser's default bullets may look plain. Keep the semantic structure; CSS can change presentation later.

## 7.5 Generic containers: `div` and `span`

`div` is a generic block-level container with no special meaning:

```html
<div class="contact-card">
  <p>Ana Reyes</p>
  <p>ana@example.com</p>
</div>
```

`span` is a generic inline container:

```html
<p>Room status: <span class="status">available</span></p>
```

These elements are useful styling or scripting hooks when no semantic element matches. Before choosing one, ask:

1. Is this a paragraph, list, navigation region, section, article, or other known concept?
2. Does a semantic element describe it accurately?
3. If not, is a generic grouping actually needed?

Too many generic wrappers create **div soup**: hierarchy with little communicated meaning.

## 7.6 Grouping without over-grouping

You do not need a `div` around every element:

```html
<!-- Unnecessary wrappers -->
<div>
  <h2>News</h2>
</div>
<div>
  <p>Class begins Monday.</p>
</div>
```

The following is simpler:

```html
<section>
  <h2>News</h2>
  <p>Class begins Monday.</p>
</section>
```

Chapter 10 examines `section` and other page-structure elements in depth.

## 7.7 Practice

**C07-Q1 - Semantic choice.** Choose `ul` or `ol` for (a) recipe steps and (b) available sandwich fillings.

**C07-Q2 - Fill in the blanks.**

```html
<___>
  <dt>CPU</dt>
  <___>Central Processing Unit</___>
</___>
```

**C07-Q3 - Spot the bug.** Repair the nesting:

```html
<ol>
  <li>Prepare</li>
  <ol>
    <li>Wash tools</li>
  </ol>
</ol>
```

**C07-Q4 - Tree puzzle.** In a valid unordered list, what element type should directly contain the nested `ul`?

**C07-Q5 - Semantic choice.** Should a major navigation menu be a `div`, `nav`, or `span`? Can a list appear inside your choice?

**C07-Q6 - Core challenge.** Mark up a primary navigation list with Home, Schedule, and Contact. Mark Schedule as current.

**C07-Q7 - Pause and predict.** Does `ol start="5"` create five list items, or change the first displayed number?

## Guided lab: recipe structure

Create `projects/recipe-site/index.html` with:

- One main heading and introduction.
- A description list for preparation time, cooking time, and servings.
- An unordered ingredient list.
- An ordered procedure.
- One nested list for optional toppings or variations.
- Navigation links to `index.html` and a future `contact.html`.

Use real list semantics even though the default presentation is simple.

## Stretch challenge: classify before marking up

Classify each data set, then write its markup:

1. Top five finishers in a competition.
2. Programming languages a student might choose.
3. Course code paired with course title and credits.
4. A site-wide navigation menu.
5. A paragraph containing one phrase that later needs unique styling.

For each choice, write one sentence defending the semantic relationship.

## Common misconceptions

- `ul` does not mean “bullets”; it means unordered list.
- `ol` does not mean “numbers”; it means ordered list.
- A nested list belongs inside an `li`.
- `dl` is not restricted to dictionary definitions.
- `div` and `span` are not wrong, but they communicate no domain meaning.
- Visual simplicity is not a reason to remove useful semantics.

## Chapter summary

Lists encode relationships among items: unordered membership, ordered sequence, or term-description associations. Valid nesting follows the document tree. Navigation commonly contains a list of links. Generic `div` and `span` containers are fallbacks, not default answers.

## Mastery checklist

- [ ] I choose list types by meaning.
- [ ] I nest lists inside the owning list item.
- [ ] I can write a description list.
- [ ] I can mark navigation as a list.
- [ ] I use generic containers only with a reason.

Solutions: [Content and navigation answer key](../answer-keys/02-content-and-navigation.md#chapter-7)

## Authoritative references

- [WHATWG: Grouping content](https://html.spec.whatwg.org/multipage/grouping-content.html)
- [W3C WAI: Content structure](https://www.w3.org/WAI/tutorials/page-structure/content/)

[Next: Chapter 8 - Images, Figures, and Responsive Media](08-images-figures-and-responsive-media.md)
