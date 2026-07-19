# Chapter 13: Validation and Form Submission

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Forms and Input Controls](12-forms-and-input-controls.md) | [Next: The Document Head and Metadata](14-document-head-and-metadata.md)

## Prerequisites

- Chapter 12
- Basic URL structure from Chapter 1

## Learning objectives

You will learn to:

- Add appropriate browser validation constraints.
- Distinguish required, format, length, and range validation.
- Explain GET and POST at an introductory level.
- Predict name-value submission data.
- Communicate requirements without relying only on browser errors.
- Explain why server-side validation remains necessary.
- Minimize collected data and plan confirmation, correction, and multi-step flows.

## Suggested study time

- Reading and submission tracing: 50-65 minutes
- Practice and guided lab: 45-65 minutes

## Key vocabulary

- **Constraint validation**: browser checks against declared requirements such as `required` or `min`.
- **Successful control**: a named form control whose data participates in a submission.
- **Name-value pair**: a submitted field identifier and its associated value.
- **Query string**: URL data appearing after `?`, commonly produced by GET forms.
- **Request body**: data sent within an HTTP request rather than in its URL.
- **Encoding type**: the format used to serialize submitted form data.
- **Server-side validation**: authoritative validation performed after data reaches the application server.
- **Data minimization**: collecting only information necessary for the stated purpose.

## 13.1 Validation is a conversation

Validation checks whether input meets stated requirements. Good validation prevents avoidable errors while helping users recover. It should not turn a form into a puzzle.

```html
<label for="email">Email address (required)</label>
<input id="email" name="email" type="email" required>
```

`required` prevents empty submission through normal browser validation. `type="email"` asks the browser to check basic email-address syntax. The visible label communicates the requirement before an error occurs.

Client-side validation improves experience, but it is not a security boundary. Requests can bypass the browser. A real application must validate all data again on the server.

## 13.2 Common constraints

### Length

```html
<label for="username">Username (4-20 characters)</label>
<input
  id="username"
  name="username"
  type="text"
  minlength="4"
  maxlength="20"
  required>
```

### Numeric range

```html
<label for="tickets">Tickets (1-6)</label>
<input
  id="tickets"
  name="tickets"
  type="number"
  min="1"
  max="6"
  step="1"
  required>
```

### Pattern

```html
<label for="course-code">
  Course code (three uppercase letters and three digits)
</label>
<input
  id="course-code"
  name="courseCode"
  type="text"
  pattern="[A-Z]{3}[0-9]{3}"
  title="Use three uppercase letters followed by three digits">
```

Patterns are powerful but easy to make unfriendly. State the expected format visibly and provide an example. Do not use a restrictive pattern for names or other data whose real-world variety you do not fully understand.

## 13.3 Optional, required, disabled, and readonly

- `required` means a value must be supplied.
- `disabled` makes a control unavailable and normally excludes it from submission.
- `readonly` prevents editing while allowing focus and normal text-control submission.

Do not disable a control merely to communicate information; disabled content can be difficult for some users to perceive. Explain why something is unavailable.

## 13.4 Name-value pairs

Form data is built primarily from successful controls with names:

```html
<input name="student" value="Mira">
<input name="course" value="html">
```

A simplified representation is:

```text
student=Mira
course=html
```

Unchecked checkboxes are generally absent from submission. Buttons can contribute their name/value when used to submit. Duplicate names can produce multiple values, as with checkbox groups.

## 13.5 GET

```html
<form action="/search" method="get">
```

GET submission commonly encodes data into the URL query:

```text
/search?q=semantic+html
```

GET suits retrieval actions such as searches and filters because the resulting URL can often be bookmarked and shared. Query data appears in URLs and history. Never use GET for secrets such as passwords.

## 13.6 POST

```html
<form action="/registrations" method="post">
```

POST sends form data in the request body. It commonly creates or changes server-side state and supports larger or more complex payloads. POST is not automatically encrypted. HTTPS protects data in transit; the method alone does not.

Method choice is an application and server decision, not merely an HTML styling preference.

## 13.7 Encoding and file uploads

Most ordinary forms use URL-encoded data by default. A file upload requires:

```html
<form action="/applications" method="post" enctype="multipart/form-data">
  <label for="resume">Resume (PDF)</label>
  <input id="resume" name="resume" type="file" accept=".pdf,application/pdf">
  <button type="submit">Apply</button>
</form>
```

`accept` guides file selection but does not prove that a file is safe or truly has the claimed format. The server must verify type, size, content, and storage rules.

## 13.8 Form-level and submit-button settings

The form can disable browser constraint validation:

```html
<form action="/register" method="post" novalidate>
```

Do this only when another system provides complete, accessible validation. `novalidate` is not a repair for incorrect constraints.

A submit button can override selected form settings:

```html
<button type="submit">Submit registration</button>
<button
  type="submit"
  formmethod="post"
  formaction="/registrations/draft"
  formnovalidate>
  Save draft
</button>
```

Related attributes include `formenctype` and `formtarget`. These are advanced tools for genuinely different submit actions. Clearly name each action and test which data and validation rules apply.

## 13.9 Error communication

Built-in browser messages vary. Requirements should be visible before submission:

```html
<p id="password-help">Use at least 12 characters.</p>
<label for="password">Password</label>
<input
  id="password"
  name="password"
  type="password"
  minlength="12"
  aria-describedby="password-help"
  required>
```

When JavaScript later adds custom errors, it must preserve focus, identify fields, describe the problem, and explain how to correct it.

## 13.10 Data minimization and privacy

Ask only for information necessary to complete the task. Every field creates effort and potential privacy risk.

Before adding a field, record:

- Why it is needed.
- Whether it must be required.
- Who receives it.
- How long it is retained.
- How a person can correct or remove it.

If a workshop only needs to confirm that participants meet an age requirement, collecting a complete birth date may be excessive. If an event is online, a postal address may be irrelevant.

HTML can communicate purpose and constraints. It cannot enforce retention, access control, deletion, or safe storage.

## 13.11 Confirmation, correction, and multi-step forms

For consequential submissions, let users review important data before committing it. After submission, provide a clear success message and a way to correct mistakes or undo reversible actions.

Long forms can be divided into logical steps:

```text
Step 1 of 3: Contact details
Step 2 of 3: Workshop choices
Step 3 of 3: Review and confirm
```

Each step needs a descriptive title, progress information, preserved data, and navigation that does not silently discard work. Implementing this flow requires server logic or JavaScript; HTML supplies the structure and controls.

Avoid unnecessary time limits. When a time limit is essential, later application design should warn users and provide extension where possible.

## 13.12 Practice

**C13-Q1 - Warm-up.** Which attribute makes a field mandatory?

**C13-Q2 - Fill in the blanks.**

```html
<input type="number" ___="1" ___="10" step="1">
```

**C13-Q3 - Method choice.** Choose GET or POST for a public search form, and explain.

**C13-Q4 - Security reasoning.** Does POST encrypt form data? What provides transport encryption?

**C13-Q5 - Submission puzzle.** Which identifier is central to the submitted pair: `id`, `class`, or `name`?

**C13-Q6 - Pause and predict.** Is an unchecked optional checkbox normally present in submitted data?

**C13-Q7 - Spot the misconception.** “HTML validation means the server can trust the data.” Correct this.

**C13-Q8 - Core challenge.** Write a required ticket control accepting whole numbers from 1 through 4 with a visible label.

**C13-Q9 - Privacy decision.** A free online seminar asks for name, email, home address, date of birth, employer, and passport number. Which principle should be applied before making fields required, and what question should be asked about each field?

## Guided lab: validate event registration

Improve Chapter 12's form:

1. Mark genuinely mandatory fields.
2. Use appropriate email, date, and number types.
3. Add sensible ranges and lengths.
4. State every requirement in visible text.
5. Add help text with `aria-describedby` where useful.
6. Try empty, malformed, minimum, maximum, and valid values.
7. Record which validation messages your browser supplies.

Do not make every field required. Ask only for information the event actually needs.

## Project 3: event-registration page

Build an accessible page with event details, a schedule table, and a registration form. It must have semantic regions, table headers, labels, a radio group, optional checkboxes, useful validation, and a clear notice that this local demo does not store submissions.

Use the [event-registration rubric](../reference/project-rubrics.md#project-3-event-registration-page).

## Common misconceptions

- Validation should explain requirements, not surprise users.
- `pattern` is not suitable for every kind of human data.
- Disabled controls and readonly controls behave differently.
- GET and POST describe request semantics, not security level.
- `accept` on a file input is guidance, not server validation.
- Browser validation cannot replace server checks.

## Chapter summary

HTML constraints catch empty, malformed, out-of-range, and wrongly sized values while visible instructions prevent errors. Form submission produces name-value data. GET commonly retrieves using a query URL; POST commonly sends changes in a request body. Real applications require HTTPS and authoritative server-side validation.

## Mastery checklist

- [ ] I apply only justified validation constraints.
- [ ] I communicate requirements visibly.
- [ ] I can predict basic name-value data.
- [ ] I can explain introductory GET and POST differences.
- [ ] I know that HTTPS, not POST, encrypts transport.
- [ ] I know browser checks are not a security boundary.
- [ ] I minimize requested data and plan review, correction, and confirmation.

Solutions: [Forms and accessibility answer key](../answer-keys/04-forms-and-accessibility.md#chapter-13)

## Authoritative references

- [WHATWG: Form submission](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#form-submission)
- [WHATWG: Constraints](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#constraints)
- [W3C WAI: Form validation](https://www.w3.org/WAI/tutorials/forms/validation/)
- [W3C WAI: Multi-page forms](https://www.w3.org/WAI/tutorials/forms/multi-page/)

[Next: Chapter 14 - The Document Head and Metadata](14-document-head-and-metadata.md)
