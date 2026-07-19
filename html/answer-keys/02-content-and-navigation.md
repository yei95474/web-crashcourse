# Answer Key 2: Content and Navigation

[Course home](../HTML_CRASH_COURSE.md)

## Chapter 5

### C05-Q1

Use `h1`. It communicates that the text is the document's main heading. `strong` marks importance and `p` marks a paragraph.

### C05-Q2

The `h4` skips levels and does not clearly express the relationship:

```html
<h1>Animals</h1>
<h2>Mammals</h2>
<h2>Birds</h2>
```

If Mammals had a subsection, that subsection could begin with `h3`.

### C05-Q3

```html
<p>Water is H<sub>2</sub>O.</p>
```

### C05-Q4

Readers see:

```text
<p>
```

The references represent literal angle brackets rather than starting an element.

### C05-Q5

- Safety warning: `strong`, because it communicates seriousness.
- Stress on “blue”: `em`, because emphasis changes the intended contrast.

### C05-Q6

```html
<time datetime="2026-08-03">August 3, 2026</time>
```

### C05-Q7

The literal quotation marks duplicate the marks browsers normally provide for `q`:

```html
<p>She answered, <q>Yes.</q></p>
```

Quotation-mark presentation can vary by language.

### C05-Q8

Use `del` for the old time and `ins` for the replacement:

```html
<p>
  Begins at
  <del datetime="2026-07-10">10:00 AM</del>
  <ins datetime="2026-07-11">9:00 AM</ins>.
</p>
```

The `datetime` values describe when each edit was made; they are optional when that information is unknown.

### Stretch challenge

One possible semantic rewrite:

```html
<h2>Course Rules</h2>
<p><strong>Important:</strong> Submit work Friday.</p>
<ul>
  <li>Item one</li>
  <li>Item two</li>
  <li>Item three</li>
</ul>
```

The exact heading level depends on the surrounding outline.

## Chapter 6

### C06-Q1

```html
<a href="about.html">About us</a>
```

### C06-Q2

```text
../images/map.png
```

From `pages`, move to the parent site directory, then enter `images`.

### C06-Q3

“Download the laboratory rules (PDF)” is better because it names the destination and format even outside surrounding context. “Click here” describes an input action rather than a destination.

### C06-Q4

```html
<a href="#fees">Jump to fees</a>
...
<h2 id="fees">Fees</h2>
```

The heading ID must be unique.

### C06-Q5

The path refers to one user's Windows computer and is not a portable web path. A project-relative path such as `about.html` is appropriate when that file sits beside the current document.

### C06-Q6

On `contact.html`, one valid pattern is:

```html
<nav aria-label="Primary">
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="about.html">About</a></li>
    <li><a href="contact.html" aria-current="page">Contact</a></li>
  </ul>
</nav>
```

The same destinations and order should appear on the other pages, with their own current item marked.

### C06-Q7

It resolves to `about.html`: enter `pages`, then immediately return to its parent. The direct `about.html` path is clearer and preferred.

### C06-Q8

In HTML source, `&` can begin a character reference. Writing `&amp;` produces the literal ampersand that separates query parameters in the interpreted URL:

```text
results.html?topic=html&level=1
```

This is HTML escaping, not percent-encoding the entire URL.

## Chapter 7

### C07-Q1

- Recipe steps: `ol`, because sequence matters.
- Available fillings: `ul`, because ordinary availability does not imply order.

### C07-Q2

```html
<dl>
  <dt>CPU</dt>
  <dd>Central Processing Unit</dd>
</dl>
```

### C07-Q3

```html
<ol>
  <li>
    Prepare
    <ol>
      <li>Wash tools</li>
    </ol>
  </li>
</ol>
```

The nested list belongs inside the `li` it expands.

### C07-Q4

An `li` should directly contain the nested `ul`.

### C07-Q5

Use `nav` for a major navigation region. A `ul` can and commonly does appear inside it. A `div` has no navigation semantics; `span` is an inline generic container.

### C07-Q6

```html
<nav aria-label="Primary">
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="schedule.html" aria-current="page">Schedule</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
</nav>
```

This is the Schedule page's version.

### C07-Q7

It changes the first displayed number to 5. It does not create extra items.

## Classification stretch

1. Top five finishers: ordered list.
2. Available language choices: unordered list, unless ranking matters.
3. Course code/title/credits: description list for a small record, or a table when comparing many courses.
4. Site navigation: `nav` containing a list of links.
5. One styling phrase: `span` when no more semantic element fits.
