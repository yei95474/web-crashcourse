# Chapter 3: Your First HTML Document

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Files, Editors, and Workspaces](02-files-editors-and-workspaces.md) | [Next: HTML Syntax and the Document Tree](04-html-syntax-and-the-document-tree.md)

## Prerequisites

- Chapters 1-2
- A course workspace open in a code editor

## Learning objectives

By the end of this chapter, you should be able to:

- Create the standard structure of an HTML document.
- Explain the purpose of the doctype, root element, head, and body.
- Set the document language, encoding, viewport, and title.
- Add a heading and paragraph.
- Save, open, and inspect the result.
- Explain standards mode and the source of default browser presentation.

## Suggested study time

- Reading and typing examples: 30-40 minutes
- Practice and guided lab: 35-50 minutes

## Key vocabulary

- **Doctype**: the declaration that selects modern HTML document handling.
- **Root element**: the outermost `html` element containing the document.
- **Head**: document information and resource links that are mostly not visible page content.
- **Body**: the document content presented to the user.
- **Metadata**: information that describes or configures a document.
- **Character encoding**: the system that maps stored bytes to characters; this book uses UTF-8.
- **Viewport**: the browser area through which a page is viewed.

## 3.1 The smallest useful page

Create `exercises/chapter-03/index.html`, then type this document by hand:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Webpage</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
    <p>I am learning how HTML gives content structure.</p>
  </body>
</html>
```

Save it and open it in your browser. You should see a large heading and a paragraph. The browser tab should say “My First Webpage.”

The indentation is for humans. It makes relationships visible. The browser generally does not require those spaces, but professional source should be readable.

## 3.2 Read the document from the outside inward

### The doctype

```html
<!doctype html>
```

The doctype tells the browser to use **standards mode**, its modern document-rendering mode. Missing or historical doctypes can trigger **quirks mode**, in which browsers imitate some old, inconsistent behaviors for legacy pages. It is a declaration, not a normal HTML element. Put it first.

### The root element

```html
<html lang="en">
</html>
```

The `html` element contains the document. `lang="en"` says that its primary human language is English. Browsers, translation systems, search tools, and screen readers can use this information. Use an appropriate language code, such as `fil` for Filipino, when the document is primarily in that language.

### The head

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Webpage</title>
</head>
```

The `head` contains information *about* the document and links to supporting resources. Most head content is not displayed in the page.

- `charset="UTF-8"` selects a character encoding that can represent a wide range of writing systems and symbols.
- The viewport setting helps a page use a mobile device's width instead of pretending to be a wide desktop page.
- `title` names the page in the browser tab, bookmarks, history, and often search results.

### The body

```html
<body>
  <h1>Hello, world!</h1>
  <p>I am learning how HTML gives content structure.</p>
</body>
```

The `body` contains the page content presented to visitors. Here, `h1` marks the main heading and `p` marks a paragraph.

Browsers apply a built-in **user-agent stylesheet**, which is why an unstyled `h1` normally appears large and bold and paragraphs have spacing. Those defaults help make documents readable; they do not turn HTML into a presentation language. Later CSS can change appearance while the HTML continues to communicate meaning.

## 3.3 Opening and closing tags

Most elements have an opening tag, content, and a closing tag:

```html
<p>This is the content.</p>
```

The slash in `</p>` marks the closing tag. The complete unit is the **element**. Later you will meet **void elements**, such as `meta` and `img`, that do not wrap content and therefore have no closing tag.

## 3.4 Attributes

An **attribute** adds information to an element:

```html
<html lang="en">
```

`lang` is the attribute name and `"en"` is its value. Put attribute values in quotation marks for consistent, readable source. Attributes belong in the opening tag.

## 3.5 Source and result are different views

Your source contains tags; the rendered page normally shows their effect rather than their literal characters. The browser converts the source into an internal document representation and applies default styles. That is why an `h1` looks large even though you wrote no CSS.

Default appearance is not semantic meaning. `h1` means “the main heading,” not “large bold text.” Chapter 5 develops this distinction.

You can inspect the page in three ways:

- **View Page Source** shows the HTML sent or loaded.
- **Developer Tools > Elements** shows the browser's interpreted document.
- Your editor shows the saved file you can change.

These views may differ when the browser repairs malformed markup or JavaScript changes the document.

## 3.6 Build an About Me page

Replace only the content inside `body`:

```html
<body>
  <h1>About Jordan</h1>
  <p>Jordan is beginning a journey into web development.</p>
  <h2>Why I am learning</h2>
  <p>I want to understand how websites are structured.</p>
  <h2>What I expect</h2>
  <p>I expect to practice, make mistakes, and improve.</p>
</body>
```

Use your own name and honest content. Keep the surrounding document structure.

## 3.7 Practice

**C03-Q1 - Fill in the blank.**

```html
<!_____ html>
```

**C03-Q2 - Warm-up.** Which section contains visible page content: `head` or `body`?

**C03-Q3 - Fill in the blank.** Complete the element that sets the browser-tab label:

```html
<_____>Study Notes</_____>
```

**C03-Q4 - Spot the bug.** Identify and repair the two structural errors:

```html
<!doctype html>
<html lang="en">
  <body>
    <title>Broken Page</title>
    <h1>Practice</h1>
  </head>
</html>
```

**C03-Q5 - Pause and predict.** Which text appears in the page and which text appears in the tab?

```html
<title>Ocean Facts</title>
...
<h1>Life Underwater</h1>
```

**C03-Q6 - Core challenge.** Write a complete document containing UTF-8 encoding, a viewport setting, the title `My Learning Journal`, one `h1`, and one paragraph.

## Guided lab: personal learning journal

1. Create `projects/about-me/index.html`.
2. Type the document structure without using editor abbreviation features.
3. Set an accurate page language.
4. Add a unique title.
5. Add your name as the main heading.
6. Write two sections: goals and interests.
7. Save, refresh, and inspect the tab and body.
8. Temporarily remove the closing `</h1>`, refresh, and observe the result.
9. Restore the correct source.

Step 8 demonstrates browser error recovery. Never depend on recovery intentionally.

## Stretch challenge: teach the skeleton

Without looking at the example, write the complete document skeleton on paper or in a blank file. Beside each line, explain its responsibility to an imaginary classmate. Compare your work with the chapter only after finishing.

## Common misconceptions

- **“The title is the main visible heading.”** `title` labels the document in the browser interface; `h1` labels the main page content.
- **“If the browser displays it, the source must be correct.”** Browsers recover from many errors.
- **“The viewport setting makes a page responsive.”** It provides appropriate mobile scaling, but responsive layout later requires CSS and suitable content.
- **“Indentation changes the hierarchy.”** Nesting tags creates hierarchy; indentation merely reveals it to readers.
- **“Every element needs a closing tag.”** Most do, but void elements do not.
- **“The heading is large because HTML is styling it.”** The heading has meaning; its initial appearance comes from the browser's default stylesheet.

## Chapter summary

A modern document begins with a doctype and an `html` root carrying the page language. The `head` describes the document; the `body` contains presented content. Metadata sets encoding, viewport behavior, and title. Most elements use paired opening and closing tags, while attributes add information.

## Mastery checklist

- [ ] I can create the complete document skeleton from memory.
- [ ] I can explain the doctype, `html`, `head`, and `body`.
- [ ] I set `lang`, UTF-8 encoding, viewport metadata, and a useful title.
- [ ] I can distinguish a tag, element, and attribute.
- [ ] I can save and inspect the rendered result.
- [ ] I can explain standards mode and why browsers give unstyled elements default appearances.

Solutions: [Foundations answer key](../answer-keys/01-foundations.md#chapter-3)

## Authoritative references

- [WHATWG: The document element](https://html.spec.whatwg.org/multipage/semantics.html#the-html-element)
- [WHATWG: Document metadata](https://html.spec.whatwg.org/multipage/semantics.html#document-metadata)

[Next: Chapter 4 - HTML Syntax and the Document Tree](04-html-syntax-and-the-document-tree.md)
