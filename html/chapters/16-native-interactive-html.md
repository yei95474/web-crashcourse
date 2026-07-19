# Chapter 16: Native Interactive HTML

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Accessible HTML](15-accessible-html.md) | [Next: Advanced Attributes and Language Features](17-advanced-attributes-and-language-features.md)

## Prerequisites

- Chapters 1-15
- Forms and accessibility fundamentals

## Learning objectives

You will learn to:

- Use disclosure widgets with `details` and `summary`.
- Understand the static HTML and scripted behavior of `dialog`.
- Recognize the Popover API's HTML attributes.
- Distinguish `progress` from `meter`.
- Choose native controls according to purpose.
- Identify when HTML alone is insufficient.

## Suggested study time

- Reading and behavior prediction: 45-60 minutes
- Practice and guided lab: 45-65 minutes

## Key vocabulary

- **Disclosure**: a control that expands or collapses associated content.
- **Dialog**: a separate interaction surface requiring deliberate opening, focus, and closing behavior.
- **Modal**: a state that prevents interaction with the rest of the document until dismissed.
- **Popover**: content displayed above other page content through native popover behavior.
- **Progress indicator**: a value representing completion of a task.
- **Meter**: a scalar measurement within a known range.
- **Output**: a result produced by a calculation or user action.
- **Fallback**: an alternative when a feature or behavior is unavailable.

## 16.1 Use built-in interaction when it matches

Browsers provide controls with established keyboard behavior and accessibility semantics. Native elements reduce the work required to create a reliable interface—but only when their defined purpose matches your content.

Do not choose a widget because it looks convenient. Ask what interaction and state it represents.

## 16.2 Disclosure with `details` and `summary`

```html
<details>
  <summary>What do I need before this course?</summary>
  <p>You need a browser, code editor, and basic file-management skills.</p>
</details>
```

The `summary` is the visible control. Activating it expands or collapses the remaining content. It is keyboard-operable without JavaScript.

Open it initially when appropriate:

```html
<details open>
  <summary>Today's announcement</summary>
  <p>The laboratory closes at 5:00 PM.</p>
</details>
```

Use disclosure for optional supporting content. Do not hide critical warnings or required instructions where users may miss them.

Related disclosure elements can share a `name` in supporting browsers so opening one closes another:

```html
<details name="faq">
  <summary>Question one</summary>
  <p>Answer one.</p>
</details>
<details name="faq">
  <summary>Question two</summary>
  <p>Answer two.</p>
</details>
```

Treat newer behavior as enhancement and check current browser support before depending on it.

## 16.3 Dialogs

`dialog` represents a dialog box or similar temporary interface:

```html
<dialog open>
  <h2>Registration received</h2>
  <p>This static example is displayed with the `open` attribute.</p>
</dialog>
```

The `open` attribute displays a non-modal dialog in plain markup. Production modal behavior normally uses JavaScript's `showModal()` and `close()` methods, which manage the top layer and expected focus behavior more appropriately than toggling `open` manually.

A dialog can contain a form that closes it:

```html
<dialog open>
  <form method="dialog">
    <p>Continue to the next lesson?</p>
    <button value="cancel">Cancel</button>
    <button value="continue">Continue</button>
  </form>
</dialog>
```

HTML alone cannot supply the full application logic that decides when to open the dialog or what to do with the result.

Do not use a dialog for ordinary content that could remain in the document. Modal interfaces interrupt users and require careful focus restoration.

## 16.4 Popovers

The Popover API can declare lightweight content shown above other page content:

```html
<button popovertarget="study-tip">Show study tip</button>

<div id="study-tip" popover>
  <p>Type every example before checking the result.</p>
</div>
```

The button targets the popover by ID. The browser supplies showing, hiding, top-layer placement, and common dismissal behavior.

Use popovers for supplementary, non-modal interface content—not for essential prose that must always be discoverable. Browser support and behavior continue to evolve; verify current documentation and test target browsers.

## 16.5 Progress

`progress` reports completion of a task:

```html
<label for="course-progress">Course progress</label>
<progress id="course-progress" value="12" max="20">12 of 20 chapters</progress>
```

`value` ranges from zero to `max`. Omitting `value` creates an indeterminate progress indicator:

```html
<progress>Loading</progress>
```

The text between tags is fallback, not necessarily the visible label. Supply a real label or nearby explanatory text.

## 16.6 Meter

`meter` represents a scalar measurement within a known range, such as storage usage or a score:

```html
<label for="quiz-score">Quiz score</label>
<meter id="quiz-score" min="0" max="100" value="84">84%</meter>
```

Optional `low`, `high`, and `optimum` values describe regions:

```html
<meter
  min="0"
  max="100"
  low="40"
  high="80"
  optimum="100"
  value="84">
  84%
</meter>
```

Do not use `meter` for task completion; that is `progress`. Do not use either as a decorative bar chart for unrelated data.

## 16.7 Output

`output` represents a calculation or user-action result:

```html
<form>
  <label for="quantity">Quantity</label>
  <input id="quantity" name="quantity" type="number" value="2">
  <output name="total" for="quantity">2 items</output>
</form>
```

Without JavaScript or a server response, the output will not update when the input changes. HTML expresses the relationship; programming supplies dynamic calculation.

## 16.8 Practice

**C16-Q1 - Semantic choice.** Which two elements create a native disclosure widget?

**C16-Q2 - Pause and predict.** What effect does `open` have on `details`?

**C16-Q3 - Semantic choice.** Use `progress` or `meter` for (a) a file upload that is 60% complete and (b) a battery charge reading.

**C16-Q4 - Fill in the blank.**

```html
<button __________="tip">Show tip</button>
<div id="tip" popover>...</div>
```

**C16-Q5 - Reasoning.** Why does a production modal dialog normally need JavaScript even though `dialog open` is valid HTML?

**C16-Q6 - Accessibility choice.** Should essential emergency instructions be hidden inside a closed disclosure by default?

**C16-Q7 - Core challenge.** Create a labeled progress element showing 7 of 10 lessons complete.

## Guided lab: course dashboard fragment

Create a semantic fragment containing:

1. A labeled progress element for chapter completion.
2. A meter for an 8-out-of-10 self-assessment.
3. Two FAQ disclosures.
4. A study-tip popover.
5. A paragraph explaining which parts work without JavaScript.

Operate every control with a keyboard.

## Stretch challenge: choose the interface

Select a normal section, disclosure, popover, dialog, progress, or meter for each:

- A privacy policy every student must read.
- Optional definitions beside a lesson.
- A confirmation requiring an immediate decision.
- Course completion.
- Current storage use.
- A permanent contact address.

Defend the choices by semantics, discoverability, interruption, and state.

## Common misconceptions

- Native interaction is useful only when its semantics match.
- `dialog open` is not a complete modal workflow.
- Popovers are not substitutes for essential document content.
- `progress` measures task completion; `meter` measures a value in a range.
- `output` does not calculate by itself.
- New features require current support checks and real testing.

## Chapter summary

HTML includes native disclosure, dialog, popover, progress, meter, and output semantics. These features provide useful behavior and accessibility foundations, but HTML does not contain application decision logic. Choose each element by the state and interaction it represents.

## Mastery checklist

- [ ] I can build a keyboard-operable disclosure.
- [ ] I understand static versus modal dialog behavior.
- [ ] I can recognize a popover target relationship.
- [ ] I distinguish `progress` and `meter`.
- [ ] I know when programming is still required.
- [ ] I verify support before relying on newer features.

Solutions: [Advanced HTML and debugging answer key](../answer-keys/05-advanced-html-and-debugging.md#chapter-16)

## Authoritative references

- [WHATWG: Interactive elements](https://html.spec.whatwg.org/multipage/interactive-elements.html)
- [WHATWG: Popovers](https://html.spec.whatwg.org/multipage/popover.html)
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)

[Next: Chapter 17 - Advanced Attributes and Language Features](17-advanced-attributes-and-language-features.md)
