# Chapter 19: Building a Multi-page Website

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Debugging, Testing, and Validation](18-debugging-testing-and-validation.md) | [Next: Capstone and Next Steps](20-capstone-and-next-steps.md)

## Prerequisites

- Chapters 1-18
- Completed or partial earlier projects

## Learning objectives

You will learn to:

- Convert a website goal into content requirements.
- Design a maintainable directory and navigation system.
- Build pages incrementally from a shared structural plan.
- Maintain consistency without a template engine.
- Apply accessibility and test planning throughout construction.
- Include performance, privacy, compatibility, and data minimization in acceptance criteria.
- Conduct a content-complete review before styling.

## Suggested study time

- Reading and planning: 45-60 minutes
- Guided construction and project work: 90-150 minutes

## Key vocabulary

- **Project brief**: a concise statement of audience, goal, scope, constraints, and success.
- **Content inventory**: a list of content that exists, is needed, or must be revised.
- **Information architecture**: the organization, labeling, and relationships of site content.
- **Page specification**: a written description of one page's purpose, sections, and requirements.
- **Acceptance criterion**: an observable condition that must be satisfied for work to be accepted.
- **Vertical slice**: one small, complete path through planning, construction, and testing.
- **Consistency**: predictable repeated structure, terminology, and behavior across pages.
- **Maintainability**: how safely and efficiently a project can be understood and changed.

## 19.1 Start with purpose and audience

Before files, write a one-sentence project brief:

> Create a four-page website that helps prospective students understand and register for a community coding workshop.

Identify:

- **Audience**: Who needs the information?
- **Goal**: What should they understand or accomplish?
- **Content**: What evidence and details support the goal?
- **Constraints**: HTML-only, local files, accessibility requirements.
- **Success**: What observable outcomes prove completion?

Do not begin with “I want a blue sidebar.” That is a presentation decision made before content requirements.

## 19.2 Content inventory

List content before assigning pages:

```text
Site identity
Workshop overview
Eligibility and prerequisites
Schedule
Instructor profiles
Frequently asked questions
Registration form
Contact details
Privacy note
```

Remove duplication and missing essentials. Then group content into pages:

```text
Home: overview and next action
Program: prerequisites, schedule, instructors
FAQ: common questions
Register: form and privacy note
```

Each page needs a clear primary purpose.

## 19.3 Information architecture

**Information architecture** organizes content so people can find and understand it. For a small course site, a shallow structure is usually best:

```text
capstone/
  index.html
  program.html
  faq.html
  register.html
  images/
    workshop-room.jpg
    instructor-ana.jpg
  files/
    program-guide.pdf
```

Keep top-level pages together unless nested sections provide real value. Simplicity reduces path errors.

## 19.4 Navigation specification

Write the navigation once as a specification:

| Label | Destination |
| --- | --- |
| Home | `index.html` |
| Program | `program.html` |
| FAQ | `faq.html` |
| Register | `register.html` |

Copy the same order and labels to each page. Change only `aria-current="page"`.

When copying shared HTML manually, changes can drift. Maintain a checklist and update every page in one focused pass. Later, server templates, site generators, or frontend frameworks can centralize shared components; do not introduce them for this HTML-only project.

## 19.5 Page specification

For each page, define:

- Filename.
- Unique title.
- `h1`.
- User question answered.
- Major sections.
- Images and their purpose.
- Links entering and leaving the page.
- Forms or tables.
- Acceptance checks.

Example:

```text
File: program.html
Title: Program and Schedule | Community Coding Workshop
H1: Program and Schedule
Answers: What will I learn, when, and where?
Sections: prerequisites, topics, schedule, instructors
Table: two-day schedule with headers and caption
Image: instructor portrait with concise alt
```

This specification prevents blank-page uncertainty.

## 19.6 Build in vertical slices

Avoid writing all pages completely before testing anything. Build one thin, working path:

1. Create all document skeletons.
2. Add unique titles and `h1` elements.
3. Add navigation to every page.
4. Test every navigation path.
5. Complete one page's semantic content.
6. Validate it and apply lessons to the next page.
7. Add media, tables, and forms.
8. Perform site-wide audits.

A **vertical slice** is a small path through several concerns that works end to end. Early navigation testing finds architectural errors before content volume hides them.

## 19.7 Consistency and intentional variation

Consistent:

- Site name.
- Primary navigation labels and order.
- Footer information.
- Filename conventions.
- Heading-level logic.
- Contact facts.

Page-specific:

- `title`, description, `h1`.
- Current-page state.
- Main content.
- Relevant secondary navigation.

Consistency is not duplication of every sentence. It is predictable structure plus accurate context.

## 19.8 Accessibility as an acceptance criterion

Add accessibility to the definition of done:

- A keyboard user can reach and operate everything.
- Every page has useful language, title, headings, and landmarks.
- Navigation is consistent and indicates the current page.
- Images have purpose-based alternatives.
- Tables expose headers.
- Forms expose names, groups, instructions, and constraints.
- Content remains understandable without color, images, audio, or mouse use.
- Third-party resources have a documented benefit and fallback.
- Form fields collect only justified data.
- Large media has deliberate dimensions, format, and loading behavior.
- Required features have a stated compatibility expectation.

These criteria are testable requirements, not aspirations.

## 19.9 Content-first review

Before CSS, view the site as plain HTML. Ask:

- Can a first-time visitor understand the site's purpose?
- Does each page answer its promised question?
- Can users find the next action?
- Does the heading outline tell a coherent story?
- Is anything meaningful conveyed only by placement or appearance?

Well-structured plain HTML should be usable. CSS will improve presentation, not rescue missing logic.

## 19.10 Planning exercises

**C19-P1 - Audience brief.** Write a one-sentence brief naming audience, goal, and site size.

**C19-P2 - Content inventory.** List at least eight content items, then group them into three to five pages.

**C19-P3 - Directory design.** Draw the complete file tree, including planned images and downloads.

**C19-P4 - Navigation matrix.** Create a table showing whether every page links to every primary destination and which item is current.

**C19-P5 - Page specifications.** Write title, `h1`, purpose, sections, and acceptance checks for every page.

**C19-Q1 - Quality classification.** Classify each review question as primarily performance, privacy, compatibility, or data minimization:

1. Does the registration form really need a complete birth date?
2. Is the 2.5 MB hero image necessary at its current size?
3. Does the required disclosure behavior work in supported browsers?
4. What visitor information reaches the embedded map provider?

These are open-ended planning activities. Use the [multi-page project rubric](../reference/project-rubrics.md#project-4-capstone-website) rather than an answer key.

## Guided build: project shell

1. Create the directories and empty page files.
2. Put a complete HTML skeleton in each file.
3. Add page-specific title, description, and `h1`.
4. Add consistent header, navigation, main, and footer structures.
5. Mark the current page.
6. Test all navigation from all pages.
7. Validate each shell before adding detailed content.

Commit or make a backup copy after this stable milestone if you know version control. Otherwise duplicate the project folder with a dated name outside the active project.

## Stretch challenge: change request

After finishing the shell, imagine a stakeholder requests a new “Policies” page and wants “FAQ” renamed “Help.” Write the exact update checklist:

- New file and metadata.
- Navigation changes on every page.
- Current-page state.
- Incoming contextual links.
- Tests.

This reveals why consistency and reusable templates matter in larger sites.

## Common misconceptions and failure modes

- Starting with visual layout before content.
- Using vague filenames such as `page3.html`.
- Testing navigation only from `index.html`.
- Copying one title and current-page marker everywhere.
- Allowing facts to disagree between pages.
- Waiting until the end to validate.
- Treating accessibility as optional polish.

## Chapter summary

A maintainable site begins with a purpose, audience, content inventory, information architecture, and page specifications. Build a working shell and navigation before filling pages. Consistent shared structures, page-specific metadata, vertical slices, and explicit acceptance criteria control complexity.

## Mastery checklist

- [ ] I can write a measurable project brief.
- [ ] I organize content before files.
- [ ] I can design a simple directory tree.
- [ ] I specify navigation and page responsibilities.
- [ ] I build and test incrementally.
- [ ] I include accessibility in completion criteria.
- [ ] I can review usability before CSS.
- [ ] I include performance, privacy, compatibility, and minimal data in project acceptance.

Solutions for deterministic review questions: [Advanced and integration answer key](../answer-keys/05-advanced-html-and-debugging.md#chapter-19)

## Authoritative references

- [W3C WAI: Planning and managing accessibility](https://www.w3.org/WAI/planning-and-managing/)
- [WHATWG HTML Living Standard](https://html.spec.whatwg.org/multipage/)

[Next: Chapter 20 - Capstone and Next Steps](20-capstone-and-next-steps.md)
