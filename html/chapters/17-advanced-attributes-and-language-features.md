# Chapter 17: Advanced Attributes and Language Features

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Native Interactive HTML](16-native-interactive-html.md) | [Next: Debugging, Testing, and Validation](18-debugging-testing-and-validation.md)

## Prerequisites

- Chapters 1-16
- Attributes, semantics, accessibility, and document trees

## Learning objectives

You will learn to:

- Use common global attributes deliberately.
- Distinguish unique IDs, reusable classes, and custom data.
- Mark changes in language and text direction.
- Apply translation, spelling, and editing hints cautiously.
- Understand content models and contextual validity.
- Recognize obsolete and presentational HTML.
- Read unfamiliar markup critically instead of copying it blindly.
- Recognize specialized hiding, inertness, and shortcut attributes with appropriate cautions.

## Suggested study time

- Reading and source analysis: 50-65 minutes
- Practice and guided lab: 40-55 minutes

## Key vocabulary

- **Global attribute**: an attribute allowed on every HTML element, subject to meaningful use.
- **Token**: one item in a space-separated attribute value such as a class list.
- **Custom data attribute**: a `data-*` attribute reserved for page-specific script data.
- **Language tag**: a code identifying the human language of content.
- **Directionality**: the order in which characters and text runs are displayed.
- **Content model**: the kinds of content an element may contain and where it may appear.
- **Obsolete feature**: old markup that conforming modern documents should not use.
- **Conformance**: agreement between a document and the authoring requirements of a standard.

## 17.1 Global attributes

A **global attribute** can be used on all HTML elements, though it may be meaningful only in certain contexts. Important examples include:

- `id`: unique document identifier.
- `class`: reusable classification tokens.
- `lang`: human language.
- `dir`: text direction.
- `title`: advisory information.
- `hidden`: content not currently relevant.
- `data-*`: custom data for scripts.
- `tabindex`: focus participation and order.
- `contenteditable`: user editing behavior.

“Allowed everywhere” does not mean “use everywhere.”

## 17.2 ID and class

```html
<section id="admissions" class="information priority">
  <h2>Admissions</h2>
</section>
```

`id` must be unique in the document. It can serve fragment links, label associations, ARIA relationships, CSS selectors, and JavaScript lookup.

`class` contains one or more reusable space-separated classifications. Many elements may share a class. Class names should describe role or purpose, not a temporary appearance:

```html
class="warning"
```

is more durable than:

```html
class="red-text"
```

Do not add IDs and classes before they serve a real purpose.

## 17.3 Custom data attributes

Custom data belongs in attributes beginning `data-`:

```html
<li data-course-id="cs101" data-credit-hours="3">
  Introduction to Computing
</li>
```

JavaScript can later read these values through an element's dataset. `data-*` carries private application data, not semantics that browsers or assistive technologies inherently understand.

Do not hide essential user-facing information only in data attributes.

## 17.4 Language changes

The root language gives a default:

```html
<html lang="en">
```

Mark passages in another language:

```html
<p>The Filipino phrase <span lang="fil">maraming salamat</span> means “thank you very much.”</p>
```

Language metadata can affect pronunciation, spelling tools, typography, translation, and search interpretation.

Use valid language tags and identify actual linguistic changes—not code, invented product names, or every borrowed word without reason.

## 17.5 Directionality

`dir` describes text direction:

```html
<p dir="rtl" lang="ar">...</p>
```

Values include `ltr`, `rtl`, and `auto`. `auto` lets the browser infer direction from content, which can be useful for user-generated text of unknown language.

For a short directionally isolated phrase within surrounding text, `bdi` can prevent its direction from disturbing nearby punctuation:

```html
<p>Winner: <bdi>اسم المستخدم</bdi> - 42 points</p>
```

`bdo` explicitly overrides direction and should be rare.

## 17.6 Translation and editing hints

The `translate` attribute tells translation systems whether content should be translated:

```html
<p>
  Enter the command
  <code translate="no">git status</code>.
</p>
```

Use `translate="no"` for product names, code, identifiers, or text whose exact spelling must remain. Do not use it to hide content or to make an entire page unavailable to multilingual readers.

`spellcheck` is a browser editing hint:

```html
<textarea
  id="reflection"
  name="reflection"
  spellcheck="true"></textarea>
```

Support and dictionaries vary. It does not validate data or guarantee correct writing.

`contenteditable` lets users edit an element's contents:

```html
<p contenteditable="true">Editable practice text</p>
```

This adds editing behavior, not a save mechanism, form submission, accessible toolbar, or safe rich-text editor. Production editing interfaces require JavaScript, focus design, sanitization, persistence, and extensive accessibility testing.

## 17.7 Hidden content

```html
<p hidden>This announcement is not currently relevant.</p>
```

The `hidden` attribute removes content from normal presentation and accessibility exposure. It is not a method for visually hiding content while keeping it available to screen readers. JavaScript may later toggle it when interface state changes.

Do not put essential static content behind `hidden`.

`hidden="until-found"` is a specialized state in which content remains hidden but can be revealed by browser find-in-page or fragment navigation in supporting environments. Treat it as progressive enhancement: research compatibility and ensure essential content remains discoverable without depending on the behavior.

The `inert` attribute prevents a subtree from receiving focus or interaction and removes it from normal accessibility navigation. Browsers use inert behavior as part of modal dialogs. Manually applying it creates a strong restriction, so do not use it as a casual visual-hiding tool or leave important content inert accidentally.

## 17.8 `tabindex`

```html
<div tabindex="0">Custom focusable region</div>
<div tabindex="-1">Programmatically focusable region</div>
```

- `tabindex="0"` places an element in the natural sequential order.
- `tabindex="-1"` removes it from sequential tabbing but allows scripted focus.
- Positive values create a separate priority order and should generally be avoided.

Making an element focusable does not make it a button, link, or control. It still lacks the role and keyboard behavior.

### `accesskey` caution

`accesskey` assigns a browser-mediated keyboard shortcut, but the activation keys vary by browser and operating system and can conflict with browser, assistive-technology, or user shortcuts. Recognition is useful when auditing old markup; routine use is usually a poor default unless a controlled environment has a tested, documented need.

## 17.9 Content models

HTML defines what content an element may contain and where it may appear. For example:

- `ul` contains `li` children.
- `p` contains phrasing content and cannot wrap arbitrary sections.
- `head` accepts metadata content.
- `a` has restrictions against nested interactive content.

Validity is contextual. An element can be real HTML but invalid in a particular parent.

This is why learning a list of tags is insufficient. You must learn relationships and use a validator when uncertain.

## 17.10 Obsolete and presentational HTML

You may encounter:

```html
<font color="red">Warning</font>
<center>Title</center>
<marquee>News</marquee>
```

These are obsolete or nonconforming approaches. Modern HTML carries meaning; CSS handles appearance and animation. Other obsolete features include layout tables, `bgcolor`, and many old frame-related elements.

Do not “modernize” by replacing every old element with `div`. First identify the content's meaning, choose semantic HTML, then apply CSS separately.

Some valid elements are uncommon rather than obsolete. Check current references before concluding that unfamiliar syntax is wrong.

## 17.11 Practice

**C17-Q1 - Classification.** Which must be unique per document: `id` or `class`?

**C17-Q2 - Fill in the blank.**

```html
<article data-________="A104">...</article>
```

Create a custom data attribute named `record-id`.

**C17-Q3 - Language reasoning.** A primarily English page contains one Filipino sentence. Where should `lang="fil"` go?

**C17-Q4 - Focus reasoning.** Does `tabindex="0"` turn a `div` into a button?

**C17-Q5 - Semantic rewrite.** Replace `<center><font color="red">Danger</font></center>` with meaningful HTML, leaving presentation for CSS.

**C17-Q6 - Validity reasoning.** Is every real HTML element valid inside every other element?

**C17-Q7 - Pause and predict.** Is content with `hidden` still normally announced by screen readers?

**C17-Q8 - Core challenge.** Write a section with unique ID `schedule`, two reusable classes, and a custom `data-term="2026-1"` attribute.

**C17-Q9 - Semantic choice.** Which attribute should protect the exact command `npm test` from translation, and does that attribute prevent users from copying it?

## Guided lab: source-code archaeology

Find an older HTML example online or in archived coursework. Without copying it into your project:

1. Identify presentational elements or attributes.
2. Identify semantic elements still useful today.
3. Draw part of its content tree.
4. Propose semantic replacements.
5. List details requiring a current reference check.

Treat unfamiliar code as evidence to analyze, not authority to imitate.

## Stretch challenge: multilingual score list

Create a list of usernames that may contain left-to-right or right-to-left text. Use page language, local language changes where known, and `bdi` around unpredictable usernames. Explain which information HTML can know and which remains application data.

## Common misconceptions

- A global attribute is not automatically useful everywhere.
- IDs are unique; classes are reusable.
- `data-*` does not create public semantic meaning.
- Focusability is not complete interaction.
- `hidden` is not screen-reader-only content.
- Unfamiliar does not mean obsolete; verify.
- Valid elements can still be invalid in the wrong context.

## Chapter summary

Global attributes identify, classify, localize, direct, hide, focus, or attach application data to elements. Their power requires deliberate use. Contextual content models govern valid relationships, while modern semantic HTML replaces obsolete presentational markup.

## Mastery checklist

- [ ] I distinguish IDs, classes, and custom data.
- [ ] I mark document and local language correctly.
- [ ] I understand basic directionality tools.
- [ ] I use `hidden` and `tabindex` cautiously.
- [ ] I know validity depends on context.
- [ ] I can recognize and replace obsolete presentational patterns.
- [ ] I understand the limits of `translate`, `spellcheck`, and `contenteditable`.
- [ ] I recognize `hidden="until-found"`, `inert`, and `accesskey` and can explain why each requires caution.

Solutions: [Advanced HTML and debugging answer key](../answer-keys/05-advanced-html-and-debugging.md#chapter-17)

## Authoritative references

- [WHATWG: Global attributes](https://html.spec.whatwg.org/multipage/dom.html#global-attributes)
- [WHATWG: Bidirectional text](https://html.spec.whatwg.org/multipage/dom.html#the-dir-attribute)
- [WHATWG: User interaction](https://html.spec.whatwg.org/multipage/interaction.html)
- [W3C: Internationalization techniques](https://www.w3.org/International/techniques/authoring-html)

[Next: Chapter 18 - Debugging, Testing, and Validation](18-debugging-testing-and-validation.md)
