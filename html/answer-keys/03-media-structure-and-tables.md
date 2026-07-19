# Answer Key 3: Media, Structure, and Tables

[Course home](../HTML_CRASH_COURSE.md)

## Chapter 8

### C08-Q1

```html
<img src="images/robot.jpg" alt="Student-built robot lifting a cube">
```

### C08-Q2

Use an empty alt attribute: `alt=""`. Omitting the attribute can cause assistive technology to announce an unhelpful filename. A visual description would add noise when the divider has no information.

### C08-Q3

`alt="Shopping cart"` is better. Because the image is the link's only content, the alternative should name the destination or action rather than its visual form.

### C08-Q4

The source is a local Windows filesystem path and is not portable. The image also lacks an `alt` attribute. A repair might be:

```html
<img src="images/dog.jpg" alt="Dog resting beside a window">
```

The actual alt must match the image's purpose.

### C08-Q5

`figcaption`

### C08-Q6

The `img` element supplies the fallback image and accessible alternative.

### C08-Q7

```html
<img
  src="images/workshop.jpg"
  alt="Students assembling a small robot during a workshop"
  width="800"
  height="600">
```

The dimensions should match the asset's intrinsic aspect ratio.

### C08-Q8

`loading="lazy"` may defer the off-screen photograph. A main hero image is likely needed immediately, so delaying it can worsen perceived loading and an important-content performance metric. Necessity, file size, dimensions, and measurement should guide the choice.

## Chapter 9

### C09-Q1

`controls`

It is a boolean attribute.

### C09-Q2

`kind="captions"`

Captions include dialogue and meaningful non-speech audio.

### C09-Q3

```html
<iframe src="map.html" title="Campus accessibility map"></iframe>
```

### C09-Q4

The browser selects a suitable source it supports. The list provides alternatives rather than instructions to play every file.

### C09-Q5

Any two well-explained reasons:

- Interferes with screen-reader audio.
- Startles users.
- Consumes data.
- Creates problems in shared or quiet spaces.
- Removes user control.
- May be blocked by browsers anyway.

### C09-Q6

Least privilege means granting only the minimum capabilities needed for a defined purpose, rather than enabling broad access by default.

### C09-Q7

```html
<audio controls>
  <source src="media/interview.mp3" type="audio/mpeg">
  <p>
    Your browser cannot play this audio.
    <a href="media/interview.mp3">Download the interview</a>.
  </p>
</audio>
```

### C09-Q8

- Privacy: loading the iframe can disclose visitor request information to the map provider even without interaction.
- Performance: an embedded map can load a nested page, scripts, tiles, and other resources.

A normal link delays those costs until the user chooses to visit.

## Chapter 10

### C10-Q1

`main`

### C10-Q2

`article`, because a complete news story can stand independently and appear in another feed or context.

### C10-Q3

`aside` describes content that is indirectly related to surrounding content. CSS, not the element, determines whether it appears right, left, inline, or elsewhere.

### C10-Q4

```html
<main>
  <h1>Course Catalog</h1>
  <section>...</section>
</main>
```

The section should normally have its own heading in complete source.

### C10-Q5

Yes to both when context supports the meaning. An article can contain thematic sections. A section can contain several independent articles, such as a “Latest News” section containing stories.

### C10-Q6

One reasonable assignment:

- Site name/introduction: body-level `header`.
- Primary links: `nav`.
- Unique article: `main` containing `article`.
- Related-links box: `aside`.
- Copyright: body-level `footer`.

### C10-Q7

Prefer native `nav`. It supplies the intended semantics directly with less markup and fewer opportunities for incorrect ARIA.

### C10-Q8

Use `search` around the search/filter interface. Do not add `role="search"` to the native element; that would redundantly restate its semantics.

## Chapter 11

### C11-Q1

No. A two-column visual layout is presentation and belongs to CSS. A table should represent genuine row-column data relationships.

### C11-Q2

```html
<table>
  <caption>Course results</caption>
  <tr>
    <th scope="col">Student</th>
    <th scope="col">Score</th>
  </tr>
</table>
```

A complete table would add data rows and commonly `thead`/`tbody`.

### C11-Q3

It says that the header applies across the other cells in its row.

### C11-Q4

Three columns: the spanned cell occupies two, and the ordinary cell occupies one.

### C11-Q5

The table lacks a caption and header cells explaining what the columns mean. It is also too incomplete to establish the broader data purpose.

### C11-Q6

```html
<table>
  <caption>Workshop capacity</caption>
  <thead>
    <tr>
      <th scope="col">Workshop</th>
      <th scope="col">Seats</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>HTML Basics</td>
      <td>24</td>
    </tr>
    <tr>
      <td>Accessible Forms</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
```

### C11-Q7

Use `th scope="row"` because the day identifies and labels the row.

### C11-Q8

First try simplifying the data, splitting the table, or using simpler row and column headers. `th` header cells and their associations remain necessary even when `colgroup` is present; column grouping does not label data.

## Checkpoint 2 guidance

A complete site should be reviewed as a system. Confirm links from both directions, not only from the homepage. Verify the image path and purpose-based alt, then inspect landmarks and heading hierarchy independently.
