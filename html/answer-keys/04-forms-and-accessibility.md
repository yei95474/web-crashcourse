# Answer Key 4: Forms and Accessibility

[Course home](../HTML_CRASH_COURSE.md)

## Chapter 12

### C12-Q1

```html
<label for="student-email">Email</label>
<input id="student-email" name="email" type="email">
```

The values match exactly.

### C12-Q2

No. A placeholder disappears during typing, may be hard to perceive, and does not provide the reliable persistent instruction of a visible associated label.

### C12-Q3

`name` identifies the field in submitted form data. Without it, the control's value is generally omitted from normal submission.

### C12-Q4

The `name` attribute with the same value on all members creates one exclusive radio group:

```html
name="mode"
```

### C12-Q5

Use `type="tel"`. A phone number is an identifier-like string, not a value for arithmetic or numeric stepping.

### C12-Q6

The controls have different names, so they belong to different groups. Repair:

```html
<input type="radio" name="mode" value="online">
<input type="radio" name="mode" value="in-person">
```

Each also needs a label.

### C12-Q7

```html
<label for="comments">Comments</label>
<textarea id="comments" name="comments" rows="5"></textarea>
```

### C12-Q8

Inside a form, a button with no declared type defaults to submit. Declare `type="button"` for a scripted non-submit action or `type="submit"` for an intentional submit control.

### C12-Q9

A membership code is an identifier, not a quantity for arithmetic, stepping, or numeric comparison. `type="text"` preserves leading zeroes, while `inputmode="numeric"` requests a convenient virtual keyboard. `pattern="[0-9]{8}"` performs the stated format constraint; `inputmode` does not validate.

## Chapter 13

### C13-Q1

`required`

### C13-Q2

```html
<input type="number" min="1" max="10" step="1">
```

### C13-Q3

GET. A search retrieves information, and the query URL can often be bookmarked or shared.

### C13-Q4

No. POST changes where request data is placed and commonly represents a state-changing action. HTTPS supplies transport encryption.

### C13-Q5

`name`

It forms the key of a submitted name-value pair.

### C13-Q6

No. An unchecked optional checkbox is generally absent from submitted form data.

### C13-Q7

Browser validation improves user experience but can be bypassed or manipulated. The server must validate every value again before trusting, storing, or acting on it.

### C13-Q8

```html
<label for="tickets">Number of tickets (1-4)</label>
<input
  id="tickets"
  name="tickets"
  type="number"
  min="1"
  max="4"
  step="1"
  required>
```

### C13-Q9

Apply data minimization. For every requested field ask, “What task requires this information, and what is the least data that can accomplish that task?” Also document whether it must be required, who receives it, retention, and correction or removal.

## Chapter 14

### C14-Q1

The document `title` normally appears in the browser tab and is also used in bookmarks, history, and other interfaces.

### C14-Q2

```html
<title>Contact | Green Garden Club</title>
```

Other concise page-specific word orders are acceptable.

### C14-Q3

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### C14-Q4

No. A search engine can choose different page text for a result snippet.

### C14-Q5

Zoom helps people with low vision and others who need larger content. Disabling it removes user control and creates an accessibility barrier.

### C14-Q6

```html
<link rel="stylesheet" href="../styles/site.css">
```

From `pages`, move to the project root, then enter `styles`.

### C14-Q7

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta
    name="description"
    content="Register for the community HTML workshop.">
  <title>Event Registration | Community HTML Workshop</title>
</head>
```

The wording should match the actual event.

### C14-Q8

No. A canonical link suggests the preferred public URL for equivalent content; it does not navigate or redirect the visitor.

### C14-Q9

No. `noindex` communicates a preference to cooperating search crawlers. It does not require authentication or prevent direct requests, sharing, logs, or discovery. Privacy requires server-enforced access control and appropriate data handling.

## Chapter 15

### C15-Q1

Prefer the native element. It already provides tested semantics and behavior.

### C15-Q2

`Shift+Tab`

### C15-Q3

Problems include:

- Missing `alt`, so the image has no intentional text alternative.
- A click handler on `img` does not provide native button keyboard behavior or role.
- There is no clear control name.

Use a real button:

```html
<button type="submit">
  <img src="submit.png" alt="">
  Submit registration
</button>
```

If the image itself communicates all text, a concise functional alt can name the action, but visible text is generally clearer.

### C15-Q4

```html
<a href="student-handbook.pdf">Download the student handbook (PDF)</a>
```

### C15-Q5

No. A role changes exposed semantics but does not add focusability, keyboard activation, or all expected state handling.

### C15-Q6

Repair the DOM/source order so its natural focus sequence is logical. Avoid positive `tabindex` as a reorder patch.

### C15-Q7

Any five relevant manual checks, such as:

- Navigate all controls by keyboard.
- Confirm visible focus.
- Inspect heading hierarchy and landmarks.
- Review link names out of context.
- Verify label-control associations.
- Check radio/checkbox group legends.
- Review error instructions and recovery.
- Zoom to 200%.
- Confirm no instruction depends on color alone.

### C15-Q8

Automated tools cannot fully judge context, language clarity, alt usefulness, logical focus, custom interaction usability, or actual human experience. They detect a valuable but limited set of machine-testable conditions.

### C15-Q9

The accessibility tree can confirm exposed names, roles, states, landmarks, headings, and relationships. It cannot certify complete usability, content clarity, keyboard behavior, or disabled-user experience; combine it with manual interaction and human evaluation.

## Checkpoint 3 guidance

Accessibility appears throughout HTML:

- Text: logical headings and meaningful semantics.
- Links: descriptive names and predictable behavior.
- Images/media: alternatives, captions, transcripts, and control.
- Regions: landmarks and skip navigation.
- Tables: captions and header associations.
- Forms: labels, groups, instructions, and errors.
- Metadata: page title, language, and zoom support.
