# Chapter 18: Debugging, Testing, and Validation

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Advanced Attributes and Language Features](17-advanced-attributes-and-language-features.md) | [Next: Building a Multi-page Website](19-building-a-multi-page-website.md)

## Prerequisites

- Chapters 1-17
- At least one multi-page practice project

## Learning objectives

You will learn to:

- Debug systematically instead of changing code at random.
- Distinguish source, parsed DOM, network, and accessibility evidence.
- Diagnose broken links and resource paths.
- Use an HTML validator constructively.
- Test content, keyboard behavior, and multiple browsers.
- Record and retest defects.
- Diagnose environment, media-type, and compatibility failures.

## Suggested study time

- Reading and demonstrations: 55-70 minutes
- Debugging practical and testing: 60-80 minutes

## Key vocabulary

- **Symptom**: the observable difference between expected and actual behavior.
- **Reproduction**: a repeatable sequence that demonstrates a problem.
- **Hypothesis**: a testable explanation for the observed evidence.
- **Isolation**: reducing a problem until the smallest relevant cause remains.
- **Validation**: checking source against formal markup rules.
- **Compatibility**: the degree to which a feature works across selected environments.
- **Regression**: a new defect introduced when previously working behavior changes.
- **Test record**: written evidence of environment, steps, results, repairs, and retesting.

## 18.1 Debugging is controlled reasoning

A **bug** is behavior or output that differs from requirements. Debugging is the process of reducing uncertainty until the cause is known.

Use this loop:

```text
Observe -> Reproduce -> Isolate -> Form a hypothesis
-> Test one change -> Verify -> Prevent recurrence
```

Random editing destroys evidence. Change one relevant variable, then observe whether the prediction came true.

## 18.2 Describe the symptom precisely

Weak: “The website is broken.”

Useful: “On `pages/contact.html`, selecting the logo requests `pages/images/logo.png`, but the file exists at `images/logo.png`.”

A useful defect report includes:

- Page and environment.
- Exact action.
- Expected result.
- Actual result.
- Whether it happens consistently.
- Relevant error, path, or screenshot.

Precision often reveals the cause before a tool is opened.

## 18.3 The fastest beginner checks

1. Did you save the file?
2. Did you refresh the correct browser tab?
3. Are you editing the file the browser opened?
4. Is the name, capitalization, and extension exact?
5. Is the path calculated from the current document?
6. Are tags nested and closed correctly?
7. Is the element valid in this parent?
8. Did the browser report a failed request?

Use the reusable [debugging checklist](../guides/debugging-checklist.md).

## 18.4 Developer Tools evidence

### Elements panel

The Elements panel shows the parsed document tree. Use it to inspect:

- Parent-child relationships.
- Attributes.
- Browser-inserted or rearranged nodes.
- Accessible names and roles when your browser exposes them.

Edits here are temporary. Refreshing restores the saved source.

### Console

Pure HTML errors do not always appear in the console, but failed resources, security policies, or future JavaScript can produce messages. Read the first relevant error, including its file and line.

### Network panel

Refresh with the panel open. Inspect:

- Requested URL.
- Status code.
- Resource type.
- Response and transfer size.

A `404` commonly means the server could not find the requested path. Local file behavior differs, but the computed URL still reveals path mistakes.

### Accessibility tree

Browser accessibility tools can show exposed names, roles, states, headings, and landmarks. Use them to confirm your semantic prediction—not as a replacement for keyboard or screen-reader testing.

## 18.5 Source versus parsed DOM

Malformed source:

```html
<p>One
<p>Two
```

The parsed tree may contain two completed paragraphs because the parser infers closures. If Developer Tools looks more correct than your file, inspect source and validate it.

Similarly, a table parser may insert a `tbody` node. Understanding parsing prevents the mistaken conclusion that the editor secretly changed your file.

## 18.6 Validation

An HTML conformance checker compares markup with standard authoring requirements. It can detect:

- Duplicate IDs.
- Invalid nesting.
- Missing required attributes.
- Obsolete elements.
- Disallowed parent-child relationships.
- Syntax errors.

Validation cannot decide whether prose is accurate, alt text is useful, or navigation makes sense.

Process validation results:

1. Fix the earliest structural error first; later errors may be consequences.
2. Read the message and location.
3. Inspect surrounding source.
4. State the violated relationship.
5. Make one repair.
6. Validate again.

Do not blindly edit until the message disappears. Understand the rule.

## 18.7 Test cases

A **test case** defines input or action and expected result.

Example for navigation:

| Test | Action | Expected |
| --- | --- | --- |
| N1 | Activate Home from Contact | `index.html` opens |
| N2 | Tab through primary navigation | Focus follows visual/logical order |
| N3 | Inspect current page | Contact has `aria-current="page"` |

For forms, test:

- Empty required field.
- Invalid email.
- Minimum and maximum allowed value.
- Keyboard selection of radio/checkbox controls.
- Valid submission attempt.

For images, test correct loading, missing-file fallback, alternative text, and whether the file size is appropriate.

## 18.8 Cross-browser and responsive checks

HTML is standardized, but controls and recovery can differ. Test at least two browser engines when possible. Resize the window and zoom to 200%. Even without CSS, check that content remains understandable and horizontal scrolling is not caused by rigid media dimensions.

Testing does not mean trying every device on Earth. Choose representative environments based on users and risk.

## 18.9 Environment and compatibility evidence

A page can behave differently under:

- `file:///` direct loading.
- A local HTTP server.
- Production HTTPS.
- Different origins or ports.
- Different media types.
- Different browser and assistive-technology versions.

When an HTTP resource fails, record the requested URL, status code, `Content-Type`, initiating page, redirects, and relevant policy messages.

A stylesheet returned as `text/html` may indicate that the server returned an error page at the stylesheet URL. A script module can fail locally because the `file:` environment does not provide the expected origin and HTTP behavior.

For an unfamiliar feature:

1. Read its current standard definition.
2. Check maintained compatibility data.
3. Define the browsers and assistive technologies the project supports.
4. Build an isolated test.
5. Test the unsupported or failure state.
6. Decide whether the feature is required, enhanced, or unsuitable.
7. Record the source and date.

Compatibility tables guide testing; they do not replace it.

## 18.10 Practice

**C18-Q1 - Order puzzle.** Put these in a sensible loop: verify, observe, isolate, test one change, form a hypothesis.

**C18-Q2 - Path diagnosis.** A page at `pages/about.html` requests `pages/images/logo.png`, but the image is at root `images/logo.png`. What source path is likely needed?

**C18-Q3 - Tool choice.** Which panel best reveals the exact requested image URL and status?

**C18-Q4 - Concept check.** Do changes in the Elements panel normally rewrite your saved file?

**C18-Q5 - Validation reasoning.** Why should you fix the earliest structural error first?

**C18-Q6 - Testing reasoning.** Give one fact validation can check and one quality judgment it cannot.

**C18-Q7 - Spot the process bug.** A student changes five paths and three tags before refreshing. Why is this weak debugging?

**C18-Q8 - Core challenge.** Write a precise defect report for a broken link, including expected and actual behavior.

**C18-Q9 - Environment diagnosis.** A stylesheet request returns status `404` with `Content-Type: text/html`. What likely happened, and which Developer Tools panel provides the strongest first evidence?

## Debugging practical

Repair this fragment:

```html
<main id="content">
  <h1>Workshop Schedule<h1>
  <p>Choose a session:
  <ul>
    <li><a href="Pages/intro.html">Introduction</li>
    <li><a href="#advanced">Advanced HTML</a>
  </ul>
  <h2 id="advanced">Advanced HTML</h3>
  <img src="images/classroom.jpg">
</main>
```

Find syntax, path-risk, and accessibility problems. Some require project context, so state assumptions rather than inventing certainty.

## Checkpoint 4

Take one earlier project and conduct a complete quality pass:

1. Validate every page.
2. Test every internal and external link.
3. Inspect all resource requests.
4. Review headings and landmarks.
5. Test keyboard navigation and controls.
6. Review image alternatives, tables, and forms.
7. Test at 200% zoom and in a second browser.
8. Record defects and retest repairs.

## Common misconceptions

- Browser recovery is not proof of conformance.
- Developer Tools edits are generally temporary.
- A validator is neither a visual tester nor accessibility certification.
- More simultaneous changes make cause-and-effect harder to see.
- Testing only the homepage misses path errors on nested pages.
- A bug report should describe evidence, not blame.

## Chapter summary

Debugging is a disciplined evidence loop. Source, parsed DOM, network requests, console messages, validators, and accessibility trees answer different questions. Precise symptoms, isolated changes, explicit test cases, and retesting turn errors into repeatable learning.

## Mastery checklist

- [ ] I can state a bug precisely.
- [ ] I change one relevant variable at a time.
- [ ] I can inspect source, DOM, network, and accessibility evidence.
- [ ] I process validator messages systematically.
- [ ] I write expected results before testing.
- [ ] I test nested pages, keyboard behavior, zoom, and multiple browsers.
- [ ] I record environment, status, media type, and compatibility evidence.

Solutions: [Advanced HTML and debugging answer key](../answer-keys/05-advanced-html-and-debugging.md#chapter-18)

## Authoritative references

- [WHATWG: HTML syntax](https://html.spec.whatwg.org/multipage/syntax.html)
- [WHATWG: Loading web pages](https://html.spec.whatwg.org/multipage/browsing-the-web.html)
- [W3C WAI: Evaluating accessibility](https://www.w3.org/WAI/test-evaluate/)
- [Nu HTML Checker](https://validator.w3.org/nu/)

[Next: Chapter 19 - Building a Multi-page Website](19-building-a-multi-page-website.md)
