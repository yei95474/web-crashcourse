# Answer Key 6: Course Assessments

[Course home](../HTML_CRASH_COURSE.md) | [Assessment](../assessments/course-assessments.md)

Use this key after completing the diagnostic or final written assessment. Equivalent wording and other conforming code solutions should receive credit when the reasoning is correct.

## Entry diagnostic

### D-Q01

HTML. It describes document structure and meaning; CSS controls presentation and JavaScript supplies programmable behavior.

### D-Q02

The browser is the client because it sends the request.

### D-Q03

`home.html`.

### D-Q04

A code editor saves controlled plain text. A word processor may insert formatting data or save a document format rather than clean HTML source.

### D-Q05

The scheme is `https`; the host is `example.org`.

### D-Q06

Confirm that the edited file was saved, then confirm that the browser refreshed the correct file or URL. Either order receives credit when both checks are present.

### D-Q07

A paragraph.

### D-Q08

No. The inner `strong` element must close before the outer `p` closes:

```html
<p>Read the <strong>instructions</strong></p>
```

### D-Q09

```text
../images/team.jpg
```

The page first moves from `pages` to the project root, then enters `images`.

### D-Q10

Useful alternative text communicates the image's purpose or equivalent information in its specific context. It is not merely a filename or an inventory of every visible detail.

### D-Q11

The label's `for` value and the control's `id` value must match.

### D-Q12

Valid answers include checking that controls and links can be reached and operated, that focus order is logical, or that no mouse-only barrier prevents use.

## Final assessment: Part A

### F-Q01

CSS owns layout and visual animation. JavaScript may control interactive or state-dependent animation behavior, but HTML alone does not perform these presentation requests.

### F-Q02

The stylesheet URL probably points to a missing resource, and the server returned an HTML error page. The status and media type both contradict the expected successful CSS response.

### F-Q03

The expected items are `<!doctype html>`, `html`, `head`, `title`, and `body`.

### F-Q04

Heading levels express hierarchy, not desired font size. Select a heading based on its relationship to surrounding sections; change appearance later with CSS.

### F-Q05

```text
../images/tree.svg
```

### F-Q06

One valid answer:

```html
<a href="handbook.pdf">Download the student handbook (PDF)</a>
```

“Read the student handbook” is also valid if downloading is not the intended emphasis.

### F-Q07

```html
alt=""
```

The empty alternative marks the image as decorative. Omitting `alt` does not communicate the same decision reliably.

### F-Q08

`article`, because the complete news story is self-contained and can stand independently.

### F-Q09

A layout table falsely represents visual positioning as tabular data, producing misleading relationships and difficult maintenance. Visual columns belong to CSS.

### F-Q10

Ask whether the passport number is genuinely necessary for the event's stated purpose and, if so, why it must be collected and protected. Unnecessary collection violates data minimization.

### F-Q11

GET, because a public search retrieves information and can produce a shareable or bookmarkable query URL. Secrets do not belong in its query string.

### F-Q12

No. Browser validation is a usability aid and can be bypassed. The server must validate and safely process all received data.

## Final assessment: Part B

### F-Q13

The document has two `title` elements; it must have one descriptive title. `meta charset` should appear as early as possible in the head, conventionally before the title. One valid repair is:

```html
<head>
  <meta charset="UTF-8">
  <title>Student Robotics Club</title>
</head>
```

### F-Q14

```html
<p>Registration is <strong>required</strong></p>
```

### F-Q15

```html
<ul>
  <li>
    Media
    <ul>
      <li>Images</li>
    </ul>
  </li>
</ul>
```

The nested list must be a child of the relevant `li`, not a direct child of the outer `ul` beside it.

### F-Q16

```html
<img
  src="workshop.jpg"
  alt="Students assembling a robot during the workshop"
  width="600"
  height="400">
```

The wording of `alt` depends on the image and context. Award the alternative-text point for a plausible purpose-based description; `width` and `height` must both be present for the dimension points.

### F-Q17

```html
<table>
  <caption>Workshop schedule</caption>
  <tr><th scope="col">Day</th><th scope="col">Topic</th></tr>
  <tr><td>Monday</td><td>HTML</td></tr>
</table>
```

Adding `thead` and `tbody` is valid but not required by the question.

### F-Q18

```html
<label for="student-email">Email</label>
<input id="student-email" name="email" type="email">
```

Changing the label's `for` to `email` is also valid if `name="email"` is added. The essential requirements are matching `for`/`id` values and a submitted `name`.

### F-Q19

`type="button"`, because the control performs a non-submitting action.

### F-Q20

One defensible order is:

```text
Describe the symptom -> Reproduce the problem -> Form a hypothesis
-> Test one change -> Verify the repair
```

In practice, initial reproduction may happen before the symptom is fully described. Award credit when the sequence preserves observation, a testable explanation, one controlled change, and verification.

## Practical-examination guidance

### F-P01

Create a fresh defect set for each assessment group. Include at least one defect whose visible output appears acceptable but whose semantics or accessible relationship is wrong. Do not award full credit for a changed page without a defect record and retest evidence.

### F-P02

Use the capstone rubric categories at the smaller two-page scale. Do not deduct for visual plainness. Deduct when a learner invents a table or form solely to satisfy the list despite the content not requiring one.

### F-P03

Strong responses name exact elements, attributes, files, tests, and observations. General claims such as “I made it accessible” are incomplete without evidence.

## Scoring consistency

- Accept semantically equivalent valid solutions.
- Give partial credit for correct reasoning with a minor syntax mistake.
- Require repair of critical accessibility barriers even when the numerical total is passing.
- Investigate unexplained vocabulary or code that differs sharply from the learner's demonstrated work.
- Record the criterion and evidence, not merely the point deduction.
