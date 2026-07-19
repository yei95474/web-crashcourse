# Chapter 15: Accessible HTML

[Course home](../HTML_CRASH_COURSE.md) | [Previous: The Document Head and Metadata](14-document-head-and-metadata.md) | [Next: Native Interactive HTML](16-native-interactive-html.md)

## Prerequisites

- Chapters 1-14
- Semantic structure, media alternatives, tables, and forms

## Learning objectives

You will learn to:

- Describe accessibility as a design and engineering responsibility.
- Test core page behavior with a keyboard.
- Review names, roles, values, landmarks, and headings.
- Apply accessible patterns across images, links, tables, and forms.
- Use native HTML before ARIA.
- Conduct a structured beginner accessibility audit.
- Perform an introductory assistive-technology inspection without treating it as certification.
- Structure understandable form-error summaries and recognize dynamic-announcement boundaries.

## Suggested study time

- Reading and accessibility analysis: 60-75 minutes
- Manual audit and guided lab: 60-90 minutes

## Key vocabulary

- **Accessibility**: the quality of being usable by people with varied abilities and technologies.
- **Assistive technology**: hardware or software that helps a person interact with digital content.
- **Keyboard operability**: the ability to reach and use functionality without a pointing device.
- **Focus**: the current element receiving keyboard interaction.
- **Name, role, and state**: core information exposed about an interactive element.
- **Accessibility tree**: the browser's accessibility-oriented representation of the document.
- **ARIA**: attributes and roles that supplement accessibility semantics where native HTML is insufficient.
- **Automated check**: tool-based testing that detects some, but not all, accessibility problems.

## 15.1 Accessibility is part of correctness

Web accessibility means people with disabilities can perceive, understand, navigate, and interact with content. Users may have visual, hearing, motor, speech, cognitive, neurological, or temporary impairments. They may use screen readers, magnification, switch devices, voice control, captions, custom colors, or only a keyboard.

Accessible design also helps users with slow networks, bright sunlight, a broken mouse, an injured hand, or a noisy room.

Accessibility is not a checklist pasted onto a finished site. Decisions about semantics, labels, media, and interaction begin in HTML.

## 15.2 Native semantics provide contracts

A native button provides:

- A button role.
- Keyboard focus.
- Activation with expected keys.
- A disabled state.
- A name from its content.

```html
<button type="button">Show schedule</button>
```

A clickable `div` provides none of that automatically:

```html
<div onclick="showSchedule()">Show schedule</div>
```

JavaScript could reconstruct the missing behavior, but using the native element is simpler and more reliable.

This principle is the first rule of ARIA: if a native HTML element already provides the semantics and behavior you need, use it.

## 15.3 Name, role, and state

Interactive controls must communicate:

- **Name**: what is it called? “Search,” “Email address.”
- **Role**: what is it? Button, link, checkbox, text field.
- **State/value**: is it checked, expanded, disabled, or what does it contain?

Native HTML supplies many roles and states. Labels, button text, link text, legends, and image alternatives supply names.

Inspect ambiguous text:

```html
<a href="report.pdf">Read more</a>
```

“Read more” has little meaning out of context. Improve it:

```html
<a href="report.pdf">Read the 2026 accessibility report (PDF)</a>
```

## 15.4 Keyboard testing

Put the mouse aside and test:

- `Tab`: move forward through interactive elements.
- `Shift+Tab`: move backward.
- `Enter`: activate links and buttons.
- `Space`: activate buttons and toggle checkboxes.
- Arrow keys: move within many radio groups, selects, and native widgets.

Ask:

1. Can I reach every interactive feature?
2. Is the order logical?
3. Can I see which item has focus?
4. Can I operate it with expected keys?
5. Can I escape or close anything I opened?

HTML order usually determines focus order. Do not use positive `tabindex` values to rearrange a confusing document. Repair the source order instead.

## 15.5 Page structure review

A strong page provides:

- A correct `lang` on `html`.
- A unique, descriptive `title`.
- A logical `h1`-to-subheading outline.
- Semantic landmarks.
- A skip link when repeated navigation is substantial.
- Descriptive links.

```html
<a href="#main-content">Skip to main content</a>
...
<main id="main-content">
  <h1>Workshop Registration</h1>
  ...
</main>
```

CSS later can make the skip link visually unobtrusive until focused; do not hide it from keyboard users.

## 15.6 Content review

### Images

Every `img` needs a deliberate `alt`: meaningful text for informative or functional images, empty text for decorative images, and longer nearby explanation for complex content.

### Audio and video

Provide captions, transcripts, and audio description according to content. Do not autoplay unexpected sound.

### Tables

Use tables only for data. Add captions and real row/column headers.

### Forms

Use visible labels, fieldset/legend grouping, suitable input types, clear instructions, and errors that explain recovery. Do not rely on placeholder, color, or an asterisk alone.

For a server-rendered response containing several errors, place a clearly titled summary before the form and link each message to its field:

```html
<section aria-labelledby="error-heading">
  <h2 id="error-heading">There are two problems to correct</h2>
  <ul>
    <li><a href="#email">Enter an email address.</a></li>
    <li><a href="#tickets">Choose between 1 and 4 tickets.</a></li>
  </ul>
</section>
```

Also place a specific message beside each affected field and connect it with `aria-describedby` when that relationship is not otherwise clear. Move focus deliberately only when application behavior has been designed and tested.

When JavaScript changes a status without moving focus, assistive technology may need a live announcement. Implementing reliable status messages, focus movement, and `aria-live` behavior belongs to the later JavaScript and application-accessibility layer; adding `aria-live` indiscriminately can create duplicate or disruptive announcements.

## 15.7 Color and visual presentation

Most color decisions belong to CSS, but HTML authors should understand the requirement: information must not depend on color alone.

Bad concept:

```text
Fields shown in red are required.
```

Better:

```html
<label for="email">Email address (required)</label>
<input id="email" name="email" type="email" required>
```

Color may reinforce the message later, but text and semantics carry it.

## 15.8 ARIA: a repair and extension vocabulary

ARIA adds accessibility semantics when native HTML cannot express a custom interface. Examples already used include:

```html
<nav aria-label="Primary">...</nav>
<a href="about.html" aria-current="page">About</a>
<input aria-describedby="email-help">
```

ARIA does not automatically add keyboard behavior, change appearance, or fix bad structure. Incorrect ARIA can make an interface less accessible.

Guidelines for this course:

1. Prefer a suitable native element.
2. Add ARIA only for a specific missing semantic relationship.
3. Keep values synchronized with real state.
4. Test with keyboard and, when possible, assistive technology.

## 15.9 Automated and human testing

Automated checkers can detect missing attributes, duplicate IDs, and some structural errors. They cannot reliably decide whether:

- Alt text communicates the image's actual purpose.
- Heading wording is clear.
- Focus order makes sense.
- Instructions are understandable.
- A custom interaction is usable.

Use tools as assistants, not verdict machines. Combine validation, automated checks, keyboard testing, zoom/reflow inspection, and human review.

## 15.10 Assistive-technology orientation

A browser's accessibility tree exposes information such as names, roles, states, headings, and landmarks to assistive technologies. Inspecting it helps confirm whether the browser understood your semantic intent.

Common screen readers include Narrator and NVDA on Windows, VoiceOver on Apple platforms, and TalkBack on Android. Each has its own commands and interaction model.

For a first supervised check:

1. Learn how to start and exit the chosen screen reader.
2. Navigate by heading and landmark.
3. List or visit links.
4. Complete a form.
5. Inspect an image announcement.
6. Expand a disclosure and confirm its state.

Do not judge a screen reader's unfamiliar controls as a page defect. Compare the announced semantics with your prediction. A beginner test by a sighted developer supplements rather than replaces review by experienced disabled users.

Follow the complete [browser and assistive-technology lab](../appendices/03-browser-and-assistive-technology-lab.md).

## 15.11 Practice

**C15-Q1 - Principle.** If a native element provides the needed semantics and behavior, should you prefer it or reconstruct it with `div` and ARIA?

**C15-Q2 - Keyboard check.** Which key normally moves focus backward?

**C15-Q3 - Spot the problem.** Give two accessibility problems:

```html
<img src="submit.png" onclick="submitForm()">
```

**C15-Q4 - Link rewrite.** Replace “click here” with useful link text for a student handbook PDF.

**C15-Q5 - ARIA reasoning.** Does `role="button"` automatically make a `div` keyboard-operable?

**C15-Q6 - Focus reasoning.** What should you usually change instead of adding positive `tabindex` values?

**C15-Q7 - Core challenge.** List five manual checks for a registration page.

**C15-Q8 - Testing reasoning.** Why can an automated checker not certify complete accessibility?

**C15-Q9 - Evidence reasoning.** What can an accessibility-tree inspection confirm, and why is it still insufficient to certify a page?

## Guided lab: accessibility audit

Audit Project 3:

1. Confirm title, language, landmarks, and headings.
2. Follow every link and judge its name out of context.
3. Review each image's purpose and alternative.
4. Read tables by header associations.
5. Compare every label's `for` to an input `id`.
6. Operate the page without a mouse.
7. Zoom the browser to 200% and inspect readability.
8. Run an automated browser accessibility check if available.
9. Record each issue, evidence, repair, and retest result.

## Checkpoint 3

Explain how accessibility decisions appear in every earlier topic:

- Text structure
- Links
- Images
- Media
- Semantic regions
- Tables
- Forms
- Metadata

If one answer consists only of “add ARIA,” revisit the relevant chapter.

## Common misconceptions

- Accessibility is not only for screen-reader users.
- ARIA does not add behavior or fix arbitrary markup.
- A page can pass automated checks and remain unusable.
- Keyboard access requires more than focusability; operation and visible focus matter.
- Native browser behavior is an engineering asset.

## Chapter summary

Accessible HTML communicates structure, names, roles, states, and alternatives through native semantics. Keyboard testing reveals interaction barriers; content reviews reveal unclear links, missing alternatives, and weak associations. ARIA supplements genuine gaps but cannot replace semantic HTML or human testing.

## Mastery checklist

- [ ] I regard accessibility as part of correctness.
- [ ] I can perform a keyboard-only review.
- [ ] I evaluate names, roles, states, landmarks, and headings.
- [ ] I apply accessibility principles to media, tables, and forms.
- [ ] I prefer native HTML before ARIA.
- [ ] I combine automated and manual testing.
- [ ] I can perform a cautious introductory assistive-technology inspection.
- [ ] I can design a useful static error summary and identify when dynamic announcements require later application behavior.

Solutions: [Forms and accessibility answer key](../answer-keys/04-forms-and-accessibility.md#chapter-15)

## Authoritative references

- [W3C WAI: Introduction to accessibility](https://www.w3.org/WAI/fundamentals/accessibility-intro/)
- [W3C WAI: Evaluating accessibility](https://www.w3.org/WAI/test-evaluate/)
- [WHATWG: Requirements related to ARIA](https://html.spec.whatwg.org/multipage/dom.html#requirements-related-to-aria-and-to-platform-accessibility-apis)

[Next: Chapter 16 - Native Interactive HTML](16-native-interactive-html.md)
