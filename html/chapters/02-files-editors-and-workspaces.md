# Chapter 2: Files, Editors, and Workspaces

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Understanding the Web](01-understanding-the-web.md) | [Next: Your First HTML Document](03-your-first-html-document.md)

## Prerequisites

- Chapter 1
- Basic ability to use a keyboard and mouse

## Learning objectives

By the end of this chapter, you should be able to:

- Explain the purpose of a code editor and browser.
- Create a predictable project directory.
- Recognize file names, extensions, and paths.
- Use safe naming conventions for web files.
- Open a workspace, save a file, and preview it.
- Distinguish direct file preview from a trusted local HTTP server.

## Suggested study time

- Reading and demonstrations: 35-45 minutes
- File-management practice: 30-45 minutes

## Key vocabulary

- **Plain text**: text stored without word-processor formatting instructions.
- **Code editor**: software designed to create and inspect source-code files.
- **File extension**: the ending of a filename that helps identify its format, such as `.html`.
- **Directory**: a folder that contains files and other directories.
- **Path**: directions to a file or directory from a known location.
- **Workspace**: the project directory opened as one working unit in an editor.
- **Local server**: server software running on your own computer for development and testing.

## 2.1 Your two main tools

A **code editor** edits plain text. It helps with indentation, syntax coloring, file navigation, and error detection, but it does not replace understanding. A **browser** interprets the saved HTML and presents the result.

The basic workflow is:

```text
Edit -> Save -> View or refresh -> Observe -> Edit again
```

If a change does not appear, first ask two questions: “Did I save?” and “Did I refresh the correct page?” This simple check resolves a surprising number of beginner problems.

Visual Studio Code is used in this course. Notepad, Sublime Text, or another plain-text editor can also work. A word processor such as Microsoft Word is unsuitable because it adds document formatting data rather than saving clean source text by default.

## 2.2 Files, extensions, and paths

A **file name** normally contains a base name and an extension:

```text
index.html
```

- `index` is the base name.
- `.html` is the extension.

The extension helps the operating system and tools identify the file type. On Windows, File Explorer may hide known extensions. Turn on **View > Show > File name extensions** so you can detect accidental names such as `index.html.txt`.

A **directory**, also called a folder, groups files. A **path** describes a location by naming the directories that lead to a file.

```text
html-course/chapter-02/notes.html
```

Paths are central to web development. Later, an image or link will work only when its path accurately describes the target file.

## 2.3 Professional naming conventions

Use names that are easy for humans, servers, and URLs:

- Prefer lowercase: `about.html`.
- Use hyphens between words: `contact-details.html`.
- Avoid spaces: use `my-project`, not `my project`.
- Avoid punctuation other than hyphens and periods.
- Use meaningful names: `schedule.html` is clearer than `page2.html`.
- Keep extensions accurate.

Some systems treat `Photo.jpg` and `photo.jpg` as different files even when Windows appears not to. Consistent lowercase names prevent failures when a project is published.

## 2.4 Build the course workspace

Create this structure in a location you can find:

```text
html-course/
  exercises/
    chapter-02/
  projects/
    about-me/
    recipe-site/
    event-registration/
    capstone/
  experiments/
```

Use folders for responsibility:

- `exercises` contains chapter practice.
- `projects` contains longer assessed work.
- `experiments` is a safe place for temporary tests.

Avoid deeply nested or confusing locations. A project should be easy to move as one folder.

## 2.5 Open a workspace in Visual Studio Code

1. Start Visual Studio Code.
2. Choose **File > Open Folder**.
3. Select `html-course`.
4. In the Explorer panel, open `exercises/chapter-02`.
5. Create `practice.html`.
6. Type the sentence `My editor is working.`
7. Save with `Ctrl+S` on Windows/Linux or `Command+S` on macOS.

At this point the file is plain text with an `.html` extension. It is not yet a proper HTML document; Chapter 3 will supply the structure.

Many editors place a dot on an unsaved tab. Learn your editor's saved/unsaved indicator.

## 2.6 Preview methods

### Open the file directly

Find the file in Explorer or Finder and double-click it. The browser address begins with `file:///`. After editing, save and refresh.

### Use a local development extension

An extension such as Live Server can serve files through a local address such as `http://127.0.0.1:5500`. This is convenient but optional. Do not let extension setup delay your first lessons.

### Drag the file into a browser

Dragging an HTML file onto a browser window also opens it locally.

The browser may display your current plain text even though the document is incomplete. Browsers attempt to recover from imperfect input. Recovery does not prove that your source is correct.

## 2.7 Local files and local servers

Opening a file directly commonly creates a `file:///` address. A development server creates an HTTP address such as:

```text
http://127.0.0.1:5500/
```

Both are local, but they are not identical:

- HTTP provides response status codes and media types.
- Servers can treat `index.html` as a directory default.
- Root-relative paths begin at the server origin.
- Browser origin and security rules differ.
- Later JavaScript modules and network requests may require HTTP.

Use direct file preview for early HTML when it works. Use a trusted local server when you need server-like path behavior or a later technology requires it.

Editor extensions are software. Install them only from a trusted marketplace and publisher, review their maintenance and permissions, and remove those you no longer need. A live-server extension is convenient, not part of HTML.

Common Developer Tools shortcuts are `F12` or `Ctrl+Shift+I` on Windows/Linux and `Command+Option+I` on macOS. Browser menus are equally valid when shortcuts differ.

## 2.8 A path is a set of directions

Suppose your project becomes:

```text
recipe-site/
  index.html
  pages/
    contact.html
  images/
    soup.jpg
```

From `index.html`, the image is at `images/soup.jpg`. From `pages/contact.html`, reaching the same image requires moving up one directory first: `../images/soup.jpg`.

You will practice relative paths deeply in Chapter 6. For now, notice that the correct directions depend on where you begin.

## 2.9 Practice

**C02-Q1 - Warm-up.** Which program writes source text, and which program interprets it for viewing?

**C02-Q2 - Fill in the blank.** In `class-schedule.html`, the file extension is `_____`.

**C02-Q3 - Spot the problem.** Give two reasons why `My Final Page!.HTML` is a risky web filename, then propose a better name.

**C02-Q4 - Core challenge.** Given this structure, write the path from `index.html` to `logo.png`.

```text
portfolio/
  index.html
  images/
    logo.png
```

**C02-Q5 - Core challenge.** A student edits a file, refreshes the browser, and sees the old content. List the first three checks you would make.

**C02-Q6 - Pause and predict.** Is a file visible at a `file:///` address automatically available to a friend on another computer? Explain.

**C02-Q7 - Comparison.** Name two differences between opening `file:///.../index.html` and serving the same file at `http://127.0.0.1/...`.

## 2.10 Guided lab: workspace inspection

1. Create the proposed course folder structure.
2. Show file extensions in your operating system.
3. Create `experiments/naming-practice.html`.
4. Save it and open it in a browser.
5. Rename it to `first-experiment.html`.
6. Reopen it and observe how the address changes.

Write one sentence explaining the difference between a file name and a path.

## Stretch challenge: diagnose the duplicate extension

Create a temporary text file through a basic text editor and attempt to name it `test.html`. Inspect the final filename with extensions visible. If the editor added `.txt`, determine which save option controls the file type. Remove the temporary file when finished.

The lesson is not a particular sequence of Windows clicks. The lesson is to verify what your tools actually created.

## Common misconceptions

- **“A file is saved because I typed it.”** Editing and saving are separate actions.
- **“Capitalization never matters.”** It can matter after publishing.
- **“Spaces are forbidden.”** URLs can represent spaces, but avoiding them makes paths easier and less error-prone.
- **“Live Server is HTML.”** It is a convenience tool, not part of the language.
- **“The browser edits my source.”** Developer Tools can temporarily alter the displayed page, but your saved file remains unchanged unless you edit it.

## Chapter summary

Your editor creates plain-text source files; your browser interprets them. Reliable web projects use visible extensions, meaningful lowercase names, simple directory structures, and a repeated edit-save-refresh loop. Paths describe where resources live relative to a starting location.

## Mastery checklist

- [ ] I can create and find my course workspace.
- [ ] I can see complete filenames and extensions.
- [ ] I use lowercase, hyphenated web filenames.
- [ ] I can open a folder in my code editor.
- [ ] I can save a file and preview it in a browser.
- [ ] I understand that paths depend on the starting file.
- [ ] I understand when a local server changes the testing environment.

Solutions: [Foundations answer key](../answer-keys/01-foundations.md#chapter-2)

## Authoritative references

- [MDN: Dealing with files](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Dealing_with_files)
- [MDN: How the Web works](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Web_standards/How_the_web_works)
- [WHATWG: Origin](https://html.spec.whatwg.org/multipage/browsers.html#concept-origin)

[Next: Chapter 3 - Your First HTML Document](03-your-first-html-document.md)
