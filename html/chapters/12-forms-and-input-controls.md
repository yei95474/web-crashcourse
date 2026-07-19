# Chapter 12: Forms and Input Controls

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Tables and Structured Data](11-tables-and-structured-data.md) | [Next: Validation and Form Submission](13-validation-and-form-submission.md)

## Prerequisites

- Chapters 1-11
- Attributes, semantics, and accessible labels

## Learning objectives

You will learn to:

- Create a form and choose controls according to the requested data.
- Associate every control with a visible label.
- Explain `id`, `for`, `name`, and `value`.
- Build text fields, textareas, selects, radio groups, and checkbox groups.
- Group controls with `fieldset` and `legend`.
- Use buttons with deliberate types.
- Distinguish control type, autofill purpose, and input modality.
- Use suggestions, grouped options, and multiple-value controls appropriately.
- Recognize specialized input hints and explicit form ownership.

## Suggested study time

- Reading and control comparison: 60-75 minutes
- Practice and guided lab: 60-80 minutes

## Key vocabulary

- **Form control**: an interactive element through which a user supplies or selects data.
- **Accessible name**: the name software exposes for an element to assistive technologies.
- **Label**: visible text programmatically associated with a form control.
- **Submitted name**: the control's `name`, used to identify its form-data entry.
- **Input type**: the kind of control and basic behavior requested from an `input` element.
- **Autofill**: browser assistance that reuses stored information according to its declared purpose.
- **Input modality**: the method used to enter data, such as a physical or virtual keyboard.
- **Fieldset**: a semantic group of related controls named by a `legend`.

## 12.1 Forms collect or change data

A form is an interface through which a user supplies values or requests an action:

```html
<form action="/register" method="post">
  ...
</form>
```

`action` identifies the submission destination. `method` describes how the browser sends form data. The destination does not exist in our local HTML-only projects, so submissions cannot be stored yet. You can still build and test the interface.

## 12.2 Labels are essential

```html
<p>
  <label for="full-name">Full name</label>
  <input id="full-name" name="fullName" type="text">
</p>
```

The label's `for` value exactly matches the control's `id`. This association:

- Gives the control an accessible name.
- Lets users click the label to focus or toggle the control.
- Makes the interface easier for touch and motor-impaired users.

`id` identifies an element in this document. `name` identifies the submitted field. Without `name`, a successful form control's value is generally not included in the submission.

Placeholder text is not a label. It disappears while typing, may have low contrast, and is not a reliable accessible name.

## 12.3 Input types

`input` changes behavior according to `type`:

```html
<label for="email">Email address</label>
<input id="email" name="email" type="email">

<label for="arrival">Arrival date</label>
<input id="arrival" name="arrival" type="date">

<label for="guests">Number of guests</label>
<input id="guests" name="guests" type="number" min="1" max="5">
```

Suitable types can provide mobile keyboards and built-in validation. Other common types include `password`, `tel`, `url`, `search`, `time`, and `file`.

Do not choose `number` for values that merely contain digits, such as phone numbers, account IDs, or postal codes. Arithmetic and numeric stepping do not make sense for them.

### Type, autocomplete, and input mode

Three attributes answer different questions:

- `type`: What control and validation behavior should the browser provide?
- `autocomplete`: What real-world information does the value represent?
- `inputmode`: What virtual-keyboard or input modality would be helpful?

```html
<label for="mobile">Mobile number</label>
<input
  id="mobile"
  name="mobile"
  type="tel"
  autocomplete="tel"
  inputmode="tel">
```

For an identifier containing only digits, `type="text"` can be correct while `inputmode="numeric"` requests a numeric keyboard:

```html
<label for="member-number">Eight-digit member number</label>
<input
  id="member-number"
  name="memberNumber"
  type="text"
  inputmode="numeric"
  autocomplete="off"
  pattern="[0-9]{8}">
```

`inputmode` is a hint, not validation. `autocomplete` values should accurately identify the requested information. Do not disable autofill broadly without a user-centered reason; it can save effort and help people with cognitive or motor disabilities.

Additional input hints are useful in narrower situations:

- `enterkeyhint` can suggest a virtual-keyboard Enter-key label such as `next`, `search`, or `send`.
- `autocapitalize` can hint whether a virtual keyboard should capitalize words or sentences.
- `capture` on a file input can request camera or microphone capture in supporting mobile contexts.

These hints do not validate data, guarantee a particular keyboard, or prove that captured files are safe. Test them on relevant devices and preserve an ordinary way to enter or choose the value.

## 12.4 Multiline input

`textarea` is not void; its initial value goes between tags:

```html
<label for="message">Message</label>
<textarea id="message" name="message" rows="6" cols="40"></textarea>
```

Avoid unintended whitespace between its tags when no initial value is desired.

## 12.5 Select menus

```html
<label for="topic">Workshop topic</label>
<select id="topic" name="topic">
  <option value="">Choose a topic</option>
  <option value="html">HTML</option>
  <option value="accessibility">Accessibility</option>
</select>
```

Users see the option content; submission uses its `value`. A blank first option can prompt a choice, especially when paired with `required`.

Use `optgroup` to label meaningful groups in a long menu. If users need to compare several options, visible radio buttons may work better than hiding them in a select.

```html
<label for="session">Workshop session</label>
<select id="session" name="session">
  <option value="">Choose a session</option>
  <optgroup label="Morning">
    <option value="html">HTML foundations</option>
    <option value="forms">Accessible forms</option>
  </optgroup>
  <optgroup label="Afternoon">
    <option value="media">Web media</option>
  </optgroup>
</select>
```

### Suggestions with `datalist`

`datalist` offers suggestions while allowing other valid text:

```html
<label for="city">City</label>
<input id="city" name="city" type="text" list="city-suggestions">

<datalist id="city-suggestions">
  <option value="Cebu City">
  <option value="Davao City">
  <option value="Manila">
</datalist>
```

This differs from `select`, which restricts users to supplied options unless the application provides another path. `datalist` presentation and accessibility vary, so do not use it when choosing from the list is essential and no fallback exists.

### Multiple values

Some controls accept `multiple`:

```html
<label for="documents">Supporting documents</label>
<input
  id="documents"
  name="documents"
  type="file"
  accept=".pdf,application/pdf"
  multiple>
```

A multi-select is possible:

```html
<label for="topics">Topics of interest</label>
<select id="topics" name="topics" multiple size="4">
  <option value="html">HTML</option>
  <option value="accessibility">Accessibility</option>
  <option value="testing">Testing</option>
</select>
```

Multi-select interaction can be difficult to discover, especially across operating systems. A checkbox group is often clearer for a short list.

## 12.6 Radio buttons

Radio buttons represent one choice from a group. Shared `name` values create the group:

```html
<fieldset>
  <legend>Attendance mode</legend>

  <label>
    <input type="radio" name="mode" value="in-person">
    In person
  </label>

  <label>
    <input type="radio" name="mode" value="online">
    Online
  </label>
</fieldset>
```

Each radio needs a unique value. The `legend` names the group question.

## 12.7 Checkboxes

Checkboxes represent independent yes/no choices or multiple selections:

```html
<fieldset>
  <legend>Accessibility requests</legend>

  <label>
    <input type="checkbox" name="support" value="captions">
    Live captions
  </label>

  <label>
    <input type="checkbox" name="support" value="step-free">
    Step-free access
  </label>
</fieldset>
```

Several checked controls can submit the same name with different values. A lone checkbox can represent agreement, but required legal consent must be designed carefully and never be preselected deceptively.

## 12.8 Buttons

```html
<button type="submit">Register</button>
<button type="reset">Clear form</button>
<button type="button">Preview</button>
```

- `submit` submits the form.
- `reset` restores initial values and can erase work unexpectedly; it is rarely helpful.
- `button` has no default form action and normally needs JavaScript.

Always declare the type. Inside a form, a button with no type defaults to submit.

Use a button for an action and a link for navigation.

Avoid `autofocus` unless immediate focus clearly benefits the task. Automatically moving focus can skip instructions, surprise screen-reader users, open mobile keyboards, or move the viewport before users understand the page.

### Controls associated from elsewhere

The `form` attribute can associate a control with a form elsewhere in the same document:

```html
<form id="registration" action="/register" method="post">
  <label for="student-name">Name</label>
  <input id="student-name" name="studentName">
</form>

<button type="submit" form="registration">Register</button>
```

Its value identifies the form's `id`. This can solve unusual layout or component constraints, but source order still affects reading and keyboard order. Prefer keeping related controls visibly and structurally together when possible.

## 12.9 Practice

**C12-Q1 - Fill in the blanks.**

```html
<label ___="student-email">Email</label>
<input ___="student-email" name="email" type="email">
```

**C12-Q2 - Accessibility choice.** Can `placeholder="Full name"` replace a visible label? Explain.

**C12-Q3 - Submission reasoning.** What is the main submission purpose of `name`?

**C12-Q4 - Group puzzle.** What attribute and shared value make three radio buttons one exclusive group?

**C12-Q5 - Semantic choice.** Should a phone number use `type="number"` or `type="tel"`?

**C12-Q6 - Spot the bug.** Why can both options be selected?

```html
<input type="radio" name="online" value="yes">
<input type="radio" name="in-person" value="yes">
```

**C12-Q7 - Core challenge.** Write a labeled textarea named `comments`, with five visible rows.

**C12-Q8 - Pause and predict.** What does a button without `type` do when it is inside a form?

**C12-Q9 - Attribute reasoning.** For an eight-digit membership code, explain why `type="text" inputmode="numeric"` may be better than `type="number"`. Which attribute performs actual format validation?

## Guided lab: event registration form

Create a form with:

1. Full name and email controls.
2. Event date selection.
3. One attendance-mode radio group.
4. Several optional support-request checkboxes.
5. A topic select menu.
6. A message textarea.
7. One clear submit button.

Every individual control needs a label; every radio/checkbox group needs a legend. Navigate the form using only `Tab`, arrow keys, `Space`, and `Enter`.

## Common misconceptions

- Placeholder text is not a label.
- `id` associates and identifies; `name` participates in submission.
- Radio buttons need a shared `name`, not merely visual proximity.
- A textarea's value does not use a `value` attribute.
- Buttons and links are not interchangeable.
- Form HTML does not create a database or email service.

## Chapter summary

Forms combine labeled controls into a data-entry interface. IDs connect labels, names identify submitted fields, and values represent selections. Input types should match data meaning. Fieldsets and legends identify related choices, while deliberate button types prevent accidental submission behavior.

## Mastery checklist

- [ ] Every control has a programmatically associated visible label.
- [ ] I understand `id`, `for`, `name`, and `value`.
- [ ] I choose suitable input types.
- [ ] I can build select, radio, checkbox, and textarea controls.
- [ ] I group related choices with `fieldset` and `legend`.
- [ ] I declare button types.
- [ ] I distinguish `type`, `autocomplete`, and `inputmode`.
- [ ] I can choose among `select`, `datalist`, checkboxes, and multiple-value controls.
- [ ] I recognize optional keyboard/capture hints and the form-owner `form` attribute without treating them as guarantees.

Solutions: [Forms and accessibility answer key](../answer-keys/04-forms-and-accessibility.md#chapter-12)

## Authoritative references

- [WHATWG: Forms](https://html.spec.whatwg.org/multipage/forms.html)
- [WHATWG: The input element](https://html.spec.whatwg.org/multipage/input.html)
- [W3C WAI: Forms tutorial](https://www.w3.org/WAI/tutorials/forms/)

[Next: Chapter 13 - Validation and Form Submission](13-validation-and-form-submission.md)
