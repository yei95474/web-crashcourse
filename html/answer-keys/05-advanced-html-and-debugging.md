# Answer Key 5: Advanced HTML, Debugging, and Integration

[Course home](../HTML_CRASH_COURSE.md)

## Chapter 16

### C16-Q1

`details` and `summary`

`details` contains the disclosure; `summary` is its visible control and label.

### C16-Q2

The disclosure starts expanded.

### C16-Q3

- File upload completion: `progress`.
- Battery reading: `meter`, because it is a scalar measurement in a known range rather than a task's completion state.

### C16-Q4

```html
<button popovertarget="tip">Show tip</button>
<div id="tip" popover>...</div>
```

### C16-Q5

The `open` attribute only makes the dialog displayed. Application logic must decide when to open/close it, process results, and manage focus appropriately. The dialog methods and event handling require JavaScript for a real modal workflow.

### C16-Q6

No. Critical instructions should be immediately discoverable and not depend on opening optional content.

### C16-Q7

```html
<label for="lesson-progress">Lesson progress</label>
<progress id="lesson-progress" value="7" max="10">
  7 of 10 lessons
</progress>
```

## Chapter 17

### C17-Q1

`id` must be unique in a document. A class is designed for reuse.

### C17-Q2

```html
<article data-record-id="A104">...</article>
```

### C17-Q3

Put `lang="fil"` on the smallest element that fully contains the Filipino sentence, such as its `p` or an inner `span`, while retaining the root `lang="en"`.

### C17-Q4

No. It makes the `div` part of sequential focus order but does not add button role, activation keys, disabled behavior, or other control semantics.

### C17-Q5

One semantic possibility:

```html
<p><strong>Danger</strong></p>
```

If “Danger” introduces a section, an appropriate heading level may be better. Centering and color belong to CSS, and color should not be the sole warning signal.

### C17-Q6

No. HTML content models define contextual parent-child rules.

### C17-Q7

No. Content with `hidden` is normally removed from visual and accessibility presentation while hidden.

### C17-Q8

```html
<section
  id="schedule"
  class="course-information priority"
  data-term="2026-1">
  ...
</section>
```

### C17-Q9

Use `translate="no"` on the element containing the exact command:

```html
<code translate="no">npm test</code>
```

The attribute is a translation hint. It does not prevent selection, copying, reading, or editing.

### Multilingual stretch

One pattern:

```html
<ol>
  <li><bdi>Ana</bdi> - 50 points</li>
  <li><bdi lang="ar">اسم المستخدم</bdi> - 42 points</li>
</ol>
```

`bdi` isolates unpredictable user-generated direction. Language should be added only when the application or author knows it accurately.

## Chapter 18

### C18-Q1

One sensible loop:

1. Observe.
2. Isolate.
3. Form a hypothesis.
4. Test one change.
5. Verify.

Reproduction normally occurs between observation and isolation.

### C18-Q2

```text
../images/logo.png
```

The current file is inside `pages`, so it must move to the root before entering `images`.

### C18-Q3

The Network panel.

### C18-Q4

No. Elements-panel edits are normally temporary changes to the current parsed page and disappear after refresh.

### C18-Q5

One structural error can cause the parser or validator to interpret later markup unexpectedly, producing several secondary messages. Fixing the earliest root cause can remove them.

### C18-Q6

Example:

- Can check: whether an ID is duplicated or nesting is invalid.
- Cannot judge: whether alt text accurately communicates an image's purpose.

### C18-Q7

Changing many variables destroys a clear cause-and-effect relationship. If the page changes, the student cannot know which edit mattered and may introduce additional defects.

### C18-Q8

Example defect report:

```text
Page/environment: pages/contact.html opened through local server in Firefox
Action: Activate the Home navigation link
Expected: index.html opens
Actual: A 404 page opens for /pages/index.html
Evidence: Network panel shows GET /pages/index.html -> 404
Likely cause: Link uses href="index.html" from the pages directory
Repair: Change destination to ../index.html
Retest: Home opens; status 200; keyboard activation also passes
```

### C18-Q9

The stylesheet URL likely did not identify a stylesheet; the server returned an HTML error page for the missing resource. The Network panel provides the strongest first evidence because it shows the exact requested URL, `404` status, response headers, and returned content type.

### Debugging practical

One possible repair, assuming lowercase `pages/intro.html` and an informative classroom photo:

```html
<main id="content">
  <h1>Workshop Schedule</h1>
  <p>Choose a session:</p>
  <ul>
    <li><a href="pages/intro.html">Introduction</a></li>
    <li><a href="#advanced">Advanced HTML</a></li>
  </ul>
  <h2 id="advanced">Advanced HTML</h2>
  <img
    src="images/classroom.jpg"
    alt="Students working together in the HTML classroom">
</main>
```

Repairs:

- Close `h1` correctly.
- Close `p`.
- Close the first anchor before `li`.
- Match the `h2` closing tag.
- Add an intentional image alternative.
- Verify—not merely assume—the path's capitalization and starting directory.

## Checkpoint 4 guidance

A complete quality pass produces evidence, not only a claim that the site “works.” Keep validation results, test cases, keyboard observations, defect records, and retest status. Prioritize barriers and structural errors before formatting preferences.

## Chapter 19

### C19-Q1

1. Complete birth date requirement: data minimization.
2. 2.5 MB hero image: performance.
3. Disclosure support in required browsers: compatibility.
4. Information received by an embedded map provider: privacy.

Some decisions overlap. For example, a third-party map also affects performance, but the wording asks primarily about visitor information.

## Chapter 20

### C20-Q1

HTML can describe:

- Registration and sign-in form structure.
- Labels, constraints, buttons, status text, and navigation.
- Links to confirmation or account pages.

A server or managed service must provide:

- Account creation and authentication.
- Authorization.
- Secure credential handling.
- Persistent database storage.
- Authoritative validation.
- Confirmation-token generation and email delivery.
- Abuse protection, logging, retention, and deletion.

JavaScript may enhance interaction, but it cannot turn client-side HTML into trusted permanent storage by itself.
