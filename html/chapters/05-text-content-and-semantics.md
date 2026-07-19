# Chapter 5: Text Content and Semantics

[Course home](../HTML_CRASH_COURSE.md) | [Previous: HTML Syntax and the Document Tree](04-html-syntax-and-the-document-tree.md) | [Next: Links, Paths, and Navigation](06-links-paths-and-navigation.md)

## Prerequisites

- Chapters 1-4
- Correct nesting and basic document structure

## Learning objectives

You will learn to:

- Build a logical heading hierarchy.
- Mark paragraphs, emphasis, importance, quotations, and code by meaning.
- Use abbreviations, dates, subscript, and superscript appropriately.
- Mark definitions, variables, edits, annotations, and contact information.
- Represent reserved characters safely.
- Avoid presentational and obsolete text markup.

## Suggested study time

- Reading and examples: 50-65 minutes
- Practice and guided lab: 40-55 minutes

## Key vocabulary

- **Semantics**: the meaning communicated by an element rather than its appearance.
- **Heading hierarchy**: ordered heading levels that represent document relationships.
- **Emphasis**: stress that can change the meaning of a phrase.
- **Importance**: strong significance, seriousness, or urgency.
- **Quotation**: words attributed to another source.
- **Character reference**: source notation used to represent a reserved or hard-to-type character.
- **Machine-readable value**: data written in a consistent format software can interpret.

## 5.1 Semantics: meaning that software can read

**Semantics** is meaning. In HTML, semantic elements tell browsers and assistive technologies what content *is*, not merely how it should look.

```html
<h1>Marine Biology Notes</h1>
<p>Coral reefs support diverse ecosystems.</p>
```

The first line is the page's main heading; the second is a paragraph. A browser may render them differently, but their meaning is the important distinction.

## 5.2 Headings form an outline

HTML provides `h1` through `h6`. Numbers indicate levels, not visual sizes:

```html
<h1>Student Handbook</h1>

<h2>Attendance</h2>
<h3>Excused absences</h3>
<h3>Late arrivals</h3>

<h2>Assessment</h2>
<h3>Projects</h3>
```

Use one descriptive `h1` for the main page topic in ordinary course projects. Start major sections with `h2`, and use `h3` only inside an `h2` topic. Do not jump from `h2` to `h4` because the default size looks better.

A heading should label the content that follows. Do not use a heading simply to make a sentence large, and do not use a paragraph as a fake heading.

## 5.3 Paragraphs and line breaks

Use `p` for a coherent paragraph:

```html
<p>
  The laboratory opens at 8:00 AM. Students must wear
  protective equipment.
</p>
```

Source line wrapping does not create a new displayed paragraph. Use separate `p` elements for separate paragraphs.

`br` creates a meaningful line break inside content where line division matters:

```html
<p>
  Room 204<br>
  Science Building<br>
  Central Campus
</p>
```

Do not use repeated `br` elements to create margins.

`hr` marks a thematic break, such as a shift between scenes or topics.

## 5.4 Importance, emphasis, and visual convention

```html
<p><strong>Warning:</strong> Wear eye protection.</p>
<p>I said the report is due <em>Friday</em>, not Monday.</p>
```

- `strong` marks strong importance, seriousness, or urgency.
- `em` marks stress emphasis that can change a sentence's interpretation.
- `b` draws attention without adding importance, such as a keyword in a summary.
- `i` marks text set apart in an alternate voice or convention, such as a technical term or taxonomic name.

Do not choose between these elements based only on bold or italic default styling.

## 5.5 Quotations and citations

Use `q` for a short inline quotation:

```html
<p>The guide calls practice <q>the engine of learning</q>.</p>
```

Browsers generally add quotation marks. Do not type duplicate marks around `q`.

Use `blockquote` for a longer quotation separated from surrounding prose:

```html
<blockquote cite="https://example.org/source">
  <p>Clear structure makes information easier to understand.</p>
</blockquote>
```

The `cite` attribute records a source URL for software but does not create a visible citation. Add a readable attribution when readers need one:

```html
<p>— <cite>Guide to Clear Writing</cite></p>
```

The `cite` element marks a title of a work, not normally a person's name.

## 5.6 Code and exact text

```html
<p>Use the <code>&lt;h1&gt;</code> element for the main heading.</p>
```

`code` marks computer code. `pre` preserves whitespace:

```html
<pre><code>&lt;p&gt;First line
  indented source&lt;/p&gt;</code></pre>
```

Use `kbd` for user input and `samp` for program output:

```html
<p>Press <kbd>Ctrl</kbd> + <kbd>S</kbd>.</p>
<p>The console prints <samp>Saved successfully</samp>.</p>
```

## 5.7 Specialized text semantics

```html
<p><abbr title="HyperText Markup Language">HTML</abbr> structures web content.</p>
<p>The workshop begins <time datetime="2026-08-03T09:00">August 3 at 9:00 AM</time>.</p>
<p>Water is H<sub>2</sub>O.</p>
<p>The area is 4 m<sup>2</sup>.</p>
<p><mark>Review this definition</mark> before the quiz.</p>
<p><small>Terms and conditions apply.</small></p>
```

Use specialized elements only when their meaning fits. `small` represents side comments or fine print, not any text you happen to want smaller.

## 5.8 Editorial and language-aware text

Use `dfn` for the defining occurrence of a term:

```html
<p>
  A <dfn>void element</dfn> is an element that cannot contain child content.
</p>
```

Use `var` for a mathematical or programming variable and `data` to pair visible text with a machine-readable value:

```html
<p>The area is <var>w</var> × <var>h</var>.</p>
<p>Course: <data value="CS-HTML-01">HTML Foundations</data></p>
```

Use `ins` and `del` to mark an edit:

```html
<p>
  The workshop begins at
  <del datetime="2026-07-10">10:00 AM</del>
  <ins datetime="2026-07-11">9:00 AM</ins>.
</p>
```

Do not use them merely to draw a line through text or underline it. Their meaning is insertion and deletion.

`address` contains contact information for its nearest article or for the document:

```html
<address>
  Questions? <a href="mailto:course@example.org">Email the course team</a>.
</address>
```

It is not a generic wrapper for every street address.

Some writing systems use **ruby annotations** to show pronunciation or explanatory text:

```html
<ruby>
  漢 <rp>(</rp><rt>かん</rt><rp>)</rp>
  字 <rp>(</rp><rt>じ</rt><rp>)</rp>
</ruby>
```

`rt` contains the annotation. `rp` provides fallback punctuation for older environments that do not present ruby layout.

`wbr` marks a place where a browser may break an otherwise long word or identifier:

```html
<p>Order reference: COMMUNITY<wbr>-SCIENCE<wbr>-2026<wbr>-00042</p>
```

It does not force a line break; `br` does.

## 5.9 Character references

Literal `<` and `&` can begin HTML syntax. Use **character references** when you mean the character as text:

| Character | Reference |
| --- | --- |
| `<` | `&lt;` |
| `>` | `&gt;` |
| `&` | `&amp;` |
| non-breaking space | `&nbsp;` |
| copyright | `&copy;` |

Use a normal Unicode character directly when safe and readable. Do not scatter `&nbsp;` to control layout; CSS handles spacing.

## 5.9 Practice

**C05-Q1 - Semantic choice.** Which element should mark the main page title: `h1`, `strong`, or `p`?

**C05-Q2 - Spot the problem.** Explain why this outline is confusing and repair it:

```html
<h1>Animals</h1>
<h4>Mammals</h4>
<h2>Birds</h2>
```

**C05-Q3 - Fill in the blanks.**

```html
<p>Water is H<___>2</___>O.</p>
```

**C05-Q4 - Pause and predict.** What characters should readers see?

```html
<code>&lt;p&gt;</code>
```

**C05-Q5 - Semantic choice.** Use `strong` or `em`: “The chemical is dangerous” is a safety warning; “I meant the blue folder” stresses the word blue.

**C05-Q6 - Core challenge.** Mark up a workshop date that humans read as `August 3, 2026` while software receives `2026-08-03`.

**C05-Q7 - Spot the bug.** What is redundant here?

```html
<p>She answered, "<q>Yes.</q>"</p>
```

**C05-Q8 - Editorial semantics.** Which elements should mark the old and new times in a published schedule correction?

## Guided practice: mark up a short article

Create an article titled “How I Learn.” Include:

1. One `h1`.
2. Two `h2` sections with logical order.
3. Three paragraphs.
4. One important warning and one emphasized word.
5. One abbreviation with its expansion.
6. One date with machine-readable `datetime`.
7. One code element displaying a literal HTML tag.

Read the source aloud by meaning: “main heading,” “section heading,” “paragraph,” rather than “large text,” “smaller text.”

## Project 1: About Me page

Expand the page from Chapter 3. It must contain a logical heading outline, several paragraphs, an interests section, a short quotation or motto, one machine-readable date, and clean indentation. Do not add CSS yet.

Evaluate the HTML-foundations section of the [project rubric](../reference/project-rubrics.md).

## Stretch challenge: semantic editor

Rewrite this presentational thinking as semantic HTML:

```html
<p><b>COURSE RULES</b></p>
<p><i>Important: submit work Friday.</i></p>
<p>Item one<br>Item two<br>Item three</p>
```

Choose a heading, meaningful importance/emphasis, and a real list. Lists are formally introduced in Chapter 7; research `ul` and `li` if you accept the stretch.

## Common misconceptions

- Heading numbers are not font sizes.
- `strong` and `em` communicate meaning, not merely bold and italic.
- `br` is not a general spacing tool.
- `blockquote` does not automatically provide a visible source.
- Character references are syntax for characters, not a styling mechanism.

## Chapter summary

Semantic text elements make a document's meaning machine-readable. Headings create a logical outline, paragraphs group prose, and specialized elements express importance, emphasis, quotations, code, time, and scientific notation. Character references safely represent syntax characters.

## Mastery checklist

- [ ] My heading levels form a logical outline.
- [ ] I distinguish paragraphs from line breaks.
- [ ] I choose `strong` and `em` by meaning.
- [ ] I can mark quotations and code.
- [ ] I can use `abbr`, `time`, `sub`, and `sup`.
- [ ] I can display `<`, `>`, and `&` safely.
- [ ] I can mark definitions, edits, contact information, and ruby annotations.

Solutions: [Content and navigation answer key](../answer-keys/02-content-and-navigation.md#chapter-5)

## Authoritative references

- [WHATWG: Text-level semantics](https://html.spec.whatwg.org/multipage/text-level-semantics.html)
- [WHATWG: Grouping content](https://html.spec.whatwg.org/multipage/grouping-content.html)
- [W3C WAI: Content structure](https://www.w3.org/WAI/tutorials/page-structure/content/)

[Next: Chapter 6 - Links, Paths, and Navigation](06-links-paths-and-navigation.md)
