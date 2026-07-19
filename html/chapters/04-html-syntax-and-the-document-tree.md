# Chapter 4: HTML Syntax and the Document Tree

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Your First HTML Document](03-your-first-html-document.md) | [Next: Text Content and Semantics](05-text-content-and-semantics.md)

## Prerequisites

- Chapters 1-3
- Ability to create and preview a basic document

## Learning objectives

By the end of this chapter, you should be able to:

- Distinguish tags, elements, attributes, and text nodes.
- Nest elements without overlapping tags.
- Recognize parent, child, sibling, ancestor, and descendant relationships.
- Use comments and whitespace appropriately.
- Recognize void elements and boolean attributes.
- Predict a simple document tree and explain browser parsing.

## Suggested study time

- Reading and tree tracing: 45-55 minutes
- Practice and guided lab: 35-50 minutes

## Key vocabulary

- **Syntax**: rules that describe how valid source text is written.
- **Tag**: source notation that begins or ends an HTML element.
- **Element**: a meaningful node created from HTML source.
- **Attribute**: information placed in an opening tag to configure or describe an element.
- **Nesting**: placing one element inside another without overlapping tags.
- **DOM**: the tree-like document model produced when a browser parses HTML.
- **Void element**: an element, such as `img`, that cannot contain child content.
- **Boolean attribute**: an attribute whose presence represents true, regardless of repeated text values.

## 4.1 Syntax is a shared grammar

**Syntax** is the set of rules governing how a language is written. People and browsers need shared rules so the same source has a predictable interpretation.

Consider:

```html
<p class="notice">Registration closes Friday.</p>
```

- `<p class="notice">` is the opening tag.
- `class` is an attribute.
- `"notice"` is the attribute value.
- `Registration closes Friday.` is text content.
- `</p>` is the closing tag.
- The entire unit is a `p` element.

Tags are pieces of source syntax. Elements are nodes in the interpreted document.

## 4.2 Nesting and containment

An element can contain text and other elements:

```html
<p>Please read the <strong>safety rules</strong> first.</p>
```

The `strong` element is nested inside the `p`. Close nested elements in reverse order from opening them:

```text
Open p -> open strong -> close strong -> close p
```

Incorrect overlapping:

```html
<p>Please read the <strong>safety rules</p></strong>
```

Imagine physical containers. You cannot close the outer box while an inner box is still protruding through it.

## 4.3 The document as a tree

Browsers parse HTML into a tree-like model. For this source:

```html
<body>
  <main>
    <h1>Course News</h1>
    <p>Class begins Monday.</p>
  </main>
</body>
```

A simplified tree is:

```text
body
└── main
    ├── h1
    │   └── "Course News"
    └── p
        └── "Class begins Monday."
```

Relationship vocabulary:

- `body` is the **parent** of `main`.
- `main` is a **child** of `body`.
- `h1` and `p` are **siblings**.
- `body` is an **ancestor** of `p`.
- The text inside `p` is a **descendant** of `main`.

This tree model is more than vocabulary. CSS selects nodes in it, JavaScript modifies it, and accessibility tools interpret its semantics.

The browser's in-memory representation is commonly called the **Document Object Model**, or DOM. For now, think “document tree.” Later JavaScript gives programs an interface for interacting with that tree.

## 4.4 Whitespace

Spaces, tabs, and line breaks in source are **whitespace**. In ordinary HTML text, browsers collapse consecutive whitespace into a single displayed space.

```html
<p>This       still
appears as ordinary spaced text.</p>
```

Use whitespace to make source readable, not to create visual layout. CSS will handle spacing. The `pre` element is a special case that preserves preformatted whitespace.

```html
<pre><code>line one
  line two is indented</code></pre>
```

## 4.5 Comments

Comments leave notes in source:

```html
<!-- Replace this temporary text before publishing. -->
```

The browser does not present comments as page content, but anyone who can view the source can read them. Never put passwords, private notes, keys, or confidential information in comments.

Use comments to explain *why* an unusual decision exists, mark a major section, or leave a temporary task. Avoid narrating obvious markup.

## 4.6 Void elements

Void elements cannot contain child content and do not have closing tags. Common examples include:

```html
<meta charset="UTF-8">
<img src="portrait.jpg" alt="Portrait of Ana">
<input type="email" name="email">
<br>
<hr>
```

Do not write `</img>` or wrap text inside `img`. A trailing slash such as `<img ... />` is permitted by many tools but is unnecessary in HTML; use one consistent style.

Use `br` for a meaningful line break, such as a line in an address or poem, not for adding vertical space. Use `hr` for a thematic break between parts of content, not merely a decorative line.

## 4.7 Attributes in more detail

An opening tag may have several attributes:

```html
<p id="deadline" class="notice urgent" lang="en">
  Applications close today.
</p>
```

Separate attributes with spaces. An element must not have two attributes with the same name. Some attributes accept a list of values; the `class` attribute above has the classes `notice` and `urgent`.

A **boolean attribute** represents true by being present:

```html
<input type="text" required>
```

Here, `required` is enabled by its presence. Writing `required="false"` does not disable it; the attribute is still present. Remove it to make the control optional.

## 4.8 Parsing and error recovery

**Parsing** converts source text into a structured representation. HTML defines recovery rules for malformed input, so browsers often display something instead of stopping at the first error.

This kindness can conceal problems:

```html
<p>First paragraph
<p>Second paragraph
```

A browser understands that a new `p` ends the previous paragraph. However, relying on omitted tags makes source harder for beginners to reason about. This book usually writes optional closing tags explicitly.

Developer Tools may show nodes the browser inferred or rearranged. When source and the Elements panel differ, parsing rules are a possible explanation.

## 4.9 Practice

**C04-Q1 - Warm-up.** In the example below, name the element, attribute, value, and text content.

```html
<p class="tip">Save often.</p>
```

**C04-Q2 - Spot the bug.** Correct the overlapping tags:

```html
<p>This is <em>very important.</p></em>
```

**C04-Q3 - Tree puzzle.** Given this source, which elements are siblings, and which element is the parent of `a`?

```html
<nav>
  <p>Menu</p>
  <a href="about.html">About</a>
</nav>
```

**C04-Q4 - Pause and predict.** How many ordinary spaces will a browser display between “Hello” and “world”?

```html
<p>Hello        world</p>
```

**C04-Q5 - Core challenge.** Is `required="false"` an optional field? Explain and repair it.

**C04-Q6 - Fill in the blank.** Complete the safe comment syntax:

```html
____ This note is visible only in source. ____
```

**C04-Q7 - Classification.** Which are void elements: `p`, `img`, `meta`, `strong`, `input`?

## Guided lab: draw the tree

Create this source, then draw its tree on paper:

```html
<main>
  <article>
    <h1>Tree Practice</h1>
    <p>A paragraph with <strong>important text</strong>.</p>
  </article>
  <p>Related note</p>
</main>
```

Label:

1. The parent of `article`.
2. The children of `article`.
3. The sibling of `article`.
4. One ancestor of `strong`.
5. The text child of `h1`.

Inspect the page in Developer Tools and compare its hierarchy with your drawing.

## Stretch challenge: repair a document

Correct every syntax problem while preserving the intended meaning:

```html
<body>
  <main class="lesson" class="current">
    <h1>Markup Practice<h1>
    <p>Learn <strong>one idea at a time.</p></strong>
    <img src="tree.png">A diagram</img>
    <input required="false" type="text">
  </main>
</body>
```

More than one repaired version is possible, but your image must have an `alt` attribute, nesting must not overlap, duplicate attributes must be resolved, and the input must be optional.

## Checkpoint 1

Without looking back, explain:

1. How a request and response produce a webpage.
2. Why extensions and paths matter.
3. The difference between `head` and `body`.
4. The difference between a tag and an element.
5. Why browser output alone cannot prove that source is valid.

If any answer is vague, revisit the relevant mastery checklist before Chapter 5.

## Common misconceptions

- **“Indentation creates nesting.”** Tags create nesting; indentation communicates it.
- **“Comments are private.”** They are hidden from the rendered page, not from source viewers.
- **“All whitespace is preserved.”** Ordinary text collapses it.
- **“A browser that displays the page approves the source.”** Error recovery is not validation.
- **“Boolean attributes take true and false strings.”** Presence usually means true; absence means false.

## Chapter summary

HTML source is parsed into a document tree of elements and text. Correct nesting produces clear parent-child and sibling relationships. Whitespace usually collapses, comments remain visible in source, void elements cannot contain content, and boolean attributes are enabled by presence. Browser recovery helps visitors but does not excuse malformed source.

## Mastery checklist

- [ ] I can identify tags, elements, attributes, values, and text.
- [ ] I close nested elements in reverse order.
- [ ] I can draw a simple document tree.
- [ ] I recognize common void elements.
- [ ] I understand collapsed whitespace and comments.
- [ ] I can explain boolean-attribute presence.
- [ ] I know why validation is still necessary.

Solutions: [Foundations answer key](../answer-keys/01-foundations.md#chapter-4)

## Authoritative references

- [WHATWG: HTML syntax](https://html.spec.whatwg.org/multipage/syntax.html)
- [WHATWG: Common microsyntaxes](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html)

[Next: Chapter 5 - Text Content and Semantics](05-text-content-and-semantics.md)
