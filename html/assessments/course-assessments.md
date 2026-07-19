# Course Diagnostic and Final Assessment

[Course home](../HTML_CRASH_COURSE.md) | [Assessment answer key](../answer-keys/06-course-assessments.md) | [Project rubrics](../reference/project-rubrics.md)

## Purpose

The diagnostic identifies useful starting points; it is not an entrance examination. A learner may begin Chapter 1 regardless of the score. The final assessment measures explanation, source reading, repair, construction, testing, and reflection rather than memory alone.

For both assessments:

- Work without the answer key.
- Record uncertainty instead of guessing invisibly.
- Use a plain-text editor and browser for practical work.
- If references are allowed, record which ones you used.
- Treat accessibility, privacy, and testing as part of correctness.

## Entry diagnostic

Allow 20-30 minutes. Choose or write the best answer. “I do not know yet” is a valid diagnostic response.

### Questions

**D-Q01 — Technology roles.** Which language primarily describes the structure and meaning of webpage content: HTML, CSS, or JavaScript?

**D-Q02 — Client and server.** When a browser asks another system for a webpage, which participant is the client?

**D-Q03 — Files.** Which filename is most likely an HTML document: `home.html`, `home.jpg`, or `home.docx`?

**D-Q04 — Plain text.** Why is a code editor more suitable for HTML than a word processor?

**D-Q05 — URL reading.** In `https://example.org/classes/index.html`, identify the scheme and host.

**D-Q06 — Save and refresh.** You edit a file, but the browser still shows the old sentence. Name the first two checks you should perform.

**D-Q07 — Element recognition.** In `<p>Welcome</p>`, what kind of content does `p` identify?

**D-Q08 — Nesting prediction.** Is this source correctly nested? Explain your current reasoning.

```html
<p>Read the <strong>instructions</p></strong>
```

**D-Q09 — Paths.** A page is in `pages/about.html`, and an image is in `images/team.jpg`. Which path from the page reaches the image?

**D-Q10 — Image purpose.** What information should useful `alt` text communicate?

**D-Q11 — Form association.** Which two values must match in this pattern?

```html
<label for="email">Email</label>
<input id="email" name="email" type="email">
```

**D-Q12 — Accessibility.** Give one reason to test a webpage using only a keyboard.

### Diagnostic interpretation

Count one point for each substantially correct answer.

| Score | Recommended response |
| ---: | --- |
| 0-3 | Begin at Chapter 1 and spend extra time on Chapter 2 demonstrations. |
| 4-7 | Begin at Chapter 1; some vocabulary will already be familiar. |
| 8-10 | Complete Chapters 1-4 rather than skipping them, but use the faster schedule if mastery checks are easy. |
| 11-12 | Use chapter exercises and projects as evidence; review any missed concept before accelerating. |

The score does not measure programming talent. It mainly reflects previous exposure to web and file concepts.

## Final assessment

Complete the final assessment after Chapters 1-20. Suggested time is 2-3 hours, excluding the larger capstone project.

### Part A: concepts and decisions

**F-Q01 — Technology boundary.** A stakeholder asks HTML to place two cards side by side and animate them. Which later technologies own these concerns?

**F-Q02 — Response evidence.** A requested stylesheet receives status `404` and media type `text/html`. What likely happened?

**F-Q03 — Document structure.** List the doctype and the four element names in a minimal document skeleton, including the element that supplies the required document title.

**F-Q04 — Semantics.** Explain why choosing `h2` merely because it looks smaller than `h1` is incorrect reasoning.

**F-Q05 — Relative path.** From `courses/html/lesson.html`, write a path to `courses/images/tree.svg`.

**F-Q06 — Link purpose.** Rewrite `<a href="handbook.pdf">Click here</a>` with descriptive link text.

**F-Q07 — Image decision.** What `alt` value should a purely decorative divider normally have?

**F-Q08 — Structure decision.** Choose `article` or `section` for a complete news story that could be syndicated independently, and explain.

**F-Q09 — Table decision.** Why should a two-column visual page layout not be built with a table?

**F-Q10 — Data minimization.** What question should be answered before adding a required passport-number field to an event form?

**F-Q11 — Submission.** Which method is generally suitable for a public site search, and why?

**F-Q12 — Security boundary.** Does browser constraint validation make submitted data safe for a server to trust? Explain.

### Part B: read and repair source

**F-Q13 — Document repair.** Rewrite this head so it contains early character-encoding metadata and exactly one descriptive title:

```html
<head>
  <title>Home</title>
  <meta charset="UTF-8">
  <title>Student Robotics Club</title>
</head>
```

**F-Q14 — Nesting repair.** Rewrite this fragment with valid nesting:

```html
<p>Registration is <strong>required</p></strong>
```

**F-Q15 — List repair.** Move the nested list to a valid location:

```html
<ul>
  <li>Media</li>
  <ul>
    <li>Images</li>
  </ul>
</ul>
```

**F-Q16 — Image repair.** Add the three attributes needed to provide a text alternative and reserve a 600-by-400 intrinsic area:

```html
<img src="workshop.jpg">
```

**F-Q17 — Table repair.** Change the appropriate cells into column headers with explicit scope:

```html
<table>
  <caption>Workshop schedule</caption>
  <tr><td>Day</td><td>Topic</td></tr>
  <tr><td>Monday</td><td>HTML</td></tr>
</table>
```

**F-Q18 — Form repair.** Repair the label association and ensure the control is submitted:

```html
<label for="student-email">Email</label>
<input id="email" type="email">
```

**F-Q19 — Button decision.** A button inside a form opens a non-submitting help panel with JavaScript. Which `type` should it declare?

**F-Q20 — Debugging method.** Put these actions into a defensible order: test one change, describe the symptom, verify the repair, form a hypothesis, reproduce the problem.

### Part C: practical examination

#### F-P01 — Repair practical

The instructor supplies a one-page document containing at least eight defects across syntax, paths, semantics, media alternatives, table headers, form labels, and metadata. Submit:

1. The repaired document.
2. A defect record naming each symptom, cause, repair, and retest.
3. Validator, keyboard, and link-check evidence.

Score this task out of 25 points: 15 for correct repairs, 5 for evidence, and 5 for explanations.

#### F-P02 — Construction practical

Build a two-page HTML-only information site from a short content brief. It must include:

- Complete document metadata and correct language declarations.
- Shared navigation and a skip link.
- Logical landmarks and headings.
- One purposeful image or a written justification for using none.
- One table or form only if the supplied content genuinely requires it.
- Working relative paths.
- A concise performance, privacy, compatibility, and accessibility review.

Score this task out of 35 points using the applicable criteria in the [project rubrics](../reference/project-rubrics.md).

#### F-P03 — Defense and reflection

In 300-500 words or a 5-8 minute conversation, explain:

- Two semantic choices.
- One accessibility choice.
- One defect you diagnosed using evidence.
- One feature deliberately left for CSS, JavaScript, or a server.
- The next skill you will study and why.

Score this task out of 10 points: 6 for accurate reasoning and 4 for specific evidence.

### Final scoring

| Component | Points |
| --- | ---: |
| Part A: 12 questions | 18 |
| Part B: 8 repairs | 12 |
| F-P01 repair practical | 25 |
| F-P02 construction practical | 35 |
| F-P03 defense and reflection | 10 |
| **Total** | **100** |

Recommended interpretation:

| Score | Interpretation |
| ---: | --- |
| 90-100 | Strong independent HTML mastery; ready for CSS and version control. |
| 80-89 | Meets the course standard; review weaker evidence before advancing. |
| 70-79 | Approaching mastery; repair the practical weaknesses and reassess. |
| Below 70 | Revisit the mapped chapters and complete another small project before reassessment. |

A score should never override evidence of inaccessible or copied work. Require the learner to explain submitted markup and repair critical barriers.

## Learning-outcome evidence map

| Course outcome | Primary chapters | Assessment evidence |
| --- | --- | --- |
| Explain browser requests and responses | 1-2 | D-Q01-D-Q06, F-Q02 |
| Create a conforming document | 3-4 | F-Q03, F-Q13-F-Q14, F-P01 |
| Structure text and navigation | 5-7 | F-Q04-F-Q06, F-Q15, F-P02 |
| Use media responsibly | 8-9 | F-Q07, F-Q16, F-P02 |
| Design semantic page structure | 10 | F-Q08, F-P02 |
| Represent tabular data | 11 | F-Q09, F-Q17 |
| Build and reason about forms | 12-13 | F-Q10-F-Q12, F-Q18-F-Q19 |
| Supply useful metadata | 14 | F-Q13, F-P02 |
| Audit accessibility | 15-17 | F-P01-F-P03 |
| Debug and validate systematically | 18 | F-Q20, F-P01 |
| Plan and deliver a multi-page site | 19-20 | F-P02-F-P03, capstone |

## Reassessment policy

Reassessment should use new content and equivalent criteria, not the same memorized repair file. Preserve successful evidence and repeat only the weak component unless course policy requires a complete retake.

[Assessment answer key](../answer-keys/06-course-assessments.md)
