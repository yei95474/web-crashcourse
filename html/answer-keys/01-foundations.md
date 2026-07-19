# Answer Key 1: Foundations

[Course home](../HTML_CRASH_COURSE.md)

Use these explanations after making a genuine attempt. Equivalent wording and valid alternative markup are acceptable.

## Chapter 1

### C01-Q1

The browser is the client. It initiates the request for `/about.html`; server software receives that request and returns a response.

### C01-Q2

1-c, 2-b, 3-a:

- HTML: structure and meaning.
- CSS: presentation.
- JavaScript: programmable behavior.

These responsibilities can interact, but the division is a reliable starting model.

### C01-Q3

```text
Scheme:   https
Host:     library.example.org
Path:     /books/web.html
Fragment: #chapter-2
```

There is no query in this URL.

### C01-Q4

1. The user enters a URL.
2. The browser sends a request.
3. The server sends a response.
4. The browser displays the interpreted document.

Real loading can include many more requests, redirects, caches, and processing steps.

### C01-Q5

The Internet is the connected network infrastructure used by many services. The Web is one service built on that infrastructure: interlinked resources requested with web protocols and addresses.

### C01-Q6

- `200`: success.
- `301`: redirection.
- `404`: client error; the requested resource was not found at that location.
- `503`: server error; the service is temporarily unavailable.

The first digit identifies the broad status category.

## Chapter 2

### C02-Q1

A code editor writes and saves source text. A browser parses, interprets, and presents the saved HTML.

### C02-Q2

`.html`

The period is conventionally treated as part of the extension when naming it.

### C02-Q3

Possible problems include uppercase letters, spaces, punctuation, and a vague word such as “Final.” A safer name is:

```text
final-page.html
```

An even better name describes the content, such as `course-schedule.html`.

### C02-Q4

```text
images/logo.png
```

Begin in the directory containing `index.html`, enter `images`, then name the file.

### C02-Q5

First checks:

1. Confirm the edited file was saved.
2. Refresh the correct browser tab.
3. Confirm the browser opened the same file being edited.

Next checks include duplicate project copies, cached behavior, and syntax errors.

### C02-Q6

No. A `file:///` URL refers to a location on the local machine. A friend does not have that file at the same location; it must be intentionally shared or hosted.

### C02-Q7

Any two accurate differences:

- HTTP responses provide status codes and media types.
- A server can apply directory-index behavior.
- Root-relative paths resolve against the HTTP origin.
- Browser origin rules differ.
- Some later module and request behavior works over HTTP but not `file:`.

Both addresses can still refer to files stored on the same computer.

## Chapter 3

### C03-Q1

```html
<!doctype html>
```

### C03-Q2

`body` contains presented page content. `head` contains document metadata and resource relationships.

### C03-Q3

```html
<title>Study Notes</title>
```

### C03-Q4

The example is missing an opening `head`, places `title` in `body`, and has a closing `head` with no matching opening tag. One repair:

```html
<!doctype html>
<html lang="en">
  <head>
    <title>Broken Page</title>
  </head>
  <body>
    <h1>Practice</h1>
  </body>
</html>
```

A production page should also add charset and viewport metadata.

### C03-Q5

`Ocean Facts` appears in the browser tab or related browser interface. `Life Underwater` appears as the main visible heading.

### C03-Q6

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Learning Journal</title>
  </head>
  <body>
    <h1>My Learning Journal</h1>
    <p>This journal records my HTML practice.</p>
  </body>
</html>
```

The title and heading may differ if both remain descriptive.

## Chapter 4

### C04-Q1

For `<p class="tip">Save often.</p>`:

- Element: `p`
- Attribute: `class`
- Value: `tip`
- Text content: `Save often.`

### C04-Q2

```html
<p>This is <em>very important.</em></p>
```

The inner `em` closes before the outer `p`.

### C04-Q3

`p` and `a` are siblings because both are direct children of `nav`. `nav` is the parent of `a`.

### C04-Q4

One ordinary displayed space. Consecutive source whitespace collapses in normal paragraph text.

### C04-Q5

No. A boolean attribute is true when present, regardless of the string `"false"`. Make the control optional by removing the attribute:

```html
<input type="text">
```

### C04-Q6

```html
<!-- This note is visible only in source. -->
```

Comments are not private.

### C04-Q7

Void elements: `img`, `meta`, and `input`.

Paired elements: `p` and `strong`.

### Stretch repair

One valid repair:

```html
<body>
  <main class="lesson current">
    <h1>Markup Practice</h1>
    <p>Learn <strong>one idea at a time.</strong></p>
    <img src="tree.png" alt="Diagram of a document tree">
    <input type="text">
  </main>
</body>
```

The duplicate classes became one space-separated `class` value. The heading closes correctly, nesting no longer overlaps, the void image has alt text and no closing tag, and removal of `required` makes the input optional. The precise alt text should be adjusted to the real image's purpose.

## Checkpoint 1 guidance

A strong response connects the concepts:

- A browser client requests a URL and parses the server response.
- Extensions identify file types; paths locate resources.
- `head` describes the document while `body` contains presented content.
- A tag is source syntax; an element is the interpreted document unit.
- Browsers recover from malformed HTML, so rendered output is not conformance evidence.
