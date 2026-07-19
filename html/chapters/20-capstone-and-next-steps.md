# Chapter 20: Capstone and Next Steps

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Building a Multi-page Website](19-building-a-multi-page-website.md) | Next: Continue your web-development path

## Prerequisites

- Chapters 1-19
- Completed planning artifacts from Chapter 19

## Learning objectives

You will:

- Build and assess a complete three-to-five-page HTML website.
- Demonstrate semantic, accessible, maintainable markup.
- Present evidence of testing and debugging.
- Present evidence of performance, privacy, compatibility, and data-minimization review.
- Identify gaps without confusing them with failure.
- Plan a responsible transition to CSS, JavaScript, Git, and deployment.

## Suggested study time

- Reading, planning, and self-assessment: 45-60 minutes
- Capstone construction, testing, and reflection: 4-8 hours across several sessions

## Key vocabulary

- **Capstone**: a final project integrating the course's major learning outcomes.
- **Artifact**: a file, record, plan, or result submitted as evidence of work.
- **Rubric**: criteria describing how the quality of work will be evaluated.
- **Test evidence**: recorded observations showing what was checked and what happened.
- **Defense**: an explanation of decisions, evidence, limitations, and repairs.
- **Reflection**: a reasoned account of learning, difficulties, and future improvement.
- **Deployment**: making a site available through a hosting environment.
- **Learning pathway**: a planned sequence of subjects and projects beyond the current course.

## 20.1 The capstone

Choose one:

- A personal portfolio.
- A local business or community organization.
- A student club.
- A public-information mini-site.
- Another topic approved by your instructor or justified in your project brief.

Build three to five pages. This is an HTML assessment, so visual plainness is acceptable. The evaluation concerns structure, meaning, content, usability, and correctness.

## 20.2 Required evidence

### Site-wide

- Complete modern document structure on every page.
- Accurate root language, UTF-8, and viewport metadata.
- Unique, descriptive titles and meta descriptions.
- Consistent primary navigation with current-page state.
- Semantic header, navigation, main, and footer architecture.
- Logical filenames, folders, and relative paths.

### Content

- One meaningful `h1` per page and a logical heading hierarchy.
- Paragraphs, at least one appropriate list, and descriptive links.
- At least two images with deliberate alt decisions.
- One figure with visible caption.
- At least one meaningful use of specialized text semantics such as `time`, `abbr`, `blockquote`, or `code`.

### Structured or interactive content

- One accessible table if the site's real content includes tabular data. Do not invent a table solely to satisfy a feature count; document the justified omission instead.
- One accessible form with labels, groups, names, suitable types, and reasonable constraints.
- One native interactive element such as `details`, when relevant.

### Accessibility and quality

- Keyboard-operable links, controls, and disclosures.
- No essential information available only through images, color, sound, or position.
- Useful alternatives for media.
- No obsolete presentational HTML.
- Validated pages with serious errors resolved.
- A test record covering links, keyboard behavior, forms, zoom, and at least two browsers when available.
- A resource review covering large media and third-party embeds.
- A form-field inventory explaining why personal data is requested.
- A compatibility note for any required modern feature.

## 20.3 Submission package

Organize:

```text
capstone/
  index.html
  other-pages.html
  images/
  files/
  PROJECT-NOTES.md
```

`PROJECT-NOTES.md` should contain:

1. Project brief and audience.
2. Site map.
3. Important semantic decisions.
4. Accessibility decisions.
5. Testing table with expected and actual results.
6. Known limitations.
7. What you would improve with CSS and JavaScript.
8. Performance, privacy, data-minimization, and compatibility decisions.

The course deliverables remain Markdown-focused, but your own capstone naturally consists of HTML files you create while learning.

## 20.4 Build phases

### Phase A: plan

Complete the brief, content inventory, site map, file tree, navigation specification, and page specifications.

### Phase B: structural shell

Create each document skeleton, metadata, page regions, headings, navigation, and footer. Validate.

### Phase C: content

Write useful real content. Add semantic text, links, lists, and media. Test paths from every page.

### Phase D: data and interaction

Add justified tables, forms, and native interactive content. Test with keyboard and boundary values.

### Phase E: audit

Use the debugging guide, accessibility audit, validator, and rubric. Review resources, collected data, third parties, and feature support. Record evidence, repair defects, and retest.

### Phase F: reflection

Complete project notes. Explain decisions in your own words; copying definitions is not evidence of mastery.

## 20.5 Final self-assessment

Use the [capstone rubric](../reference/project-rubrics.md#project-4-capstone-website). Score each category only after writing evidence:

```text
Criterion: Descriptive links
Evidence: Navigation labels name destinations; the PDF link includes document title and format.
Location: All pages; program.html under Resources
Test: Reviewed links out of surrounding context
```

If a criterion scores low, decide whether to repair it before submission or record it as a known limitation. Honest assessment is a professional skill.

## 20.6 Oral or written defense prompts

Answer without reading chapter definitions:

1. Why is your primary content inside `main`?
2. Show one relative path and calculate it from the current file.
3. Explain one alt-text decision based on context.
4. Demonstrate the header associations in your table.
5. Explain how a form label receives its control relationship.
6. Show the site's keyboard focus order.
7. Describe one validator error and how you repaired it.
8. Identify one place where HTML alone cannot provide the desired behavior.

If you cannot explain a copied pattern, treat it as an unfinished learning objective.

## 20.7 What “finished with HTML” means

You are ready to continue when you can:

- Start a document without copying a full template.
- Select common elements by purpose.
- Reason about the document tree.
- Calculate project paths.
- Build accessible navigation, images, tables, and forms.
- Use references for unfamiliar elements.
- Validate and debug systematically.
- Explain what belongs to CSS, JavaScript, or a server.

You do not need to memorize every element or standard rule. Professionals look up details; mastery means knowing what questions to ask and how to verify an answer.

## 20.8 Next: CSS

Study CSS in this order:

1. Selectors, declarations, properties, and values.
2. The cascade, inheritance, and specificity.
3. Color and typography.
4. The box model.
5. Normal flow.
6. Flexbox and Grid.
7. Responsive design and media queries.
8. Focus, hover, reduced motion, and accessible visual states.

Keep semantic HTML stable while CSS changes appearance. Do not replace headings, lists, or buttons with generic elements merely because styling seems easier.

## 20.9 Next: JavaScript

Begin with programming fundamentals:

1. Values, variables, expressions, and types.
2. Conditions and loops.
3. Functions.
4. Arrays and objects.
5. Errors and debugging.
6. DOM selection and events.
7. Form behavior and validation enhancement.
8. Network requests and asynchronous work.

JavaScript should enhance a working document where possible. Learn event behavior, focus management, and accessible state before building custom widgets.

## 20.10 Next: Git and GitHub

Version control records meaningful project history:

- Initialize a repository.
- Inspect status and changes.
- Stage intentional files.
- Commit one coherent change with a useful message.
- Create branches for experiments.
- Use a remote host for collaboration and backup.

Git is not the same as GitHub. Git is the version-control system; GitHub is one hosting and collaboration service.

## 20.11 Next: publishing and backend development

Static HTML/CSS/JavaScript can be hosted through many services. Publishing adds concerns such as:

- Public URLs and domain names.
- HTTPS.
- Correct case-sensitive paths.
- Caching and performance.
- Privacy and analytics.
- Security headers.
- Maintenance and broken-link review.

Saving form submissions, authenticating users, sending email, and storing data require a backend or managed service. Study HTTP, server programming, databases, validation, authentication, authorization, and security before handling real personal data.

## 20.12 How to continue learning

Use a cycle:

```text
Build -> encounter a precise problem -> consult a reliable reference
-> make a small experiment -> apply -> test -> explain
```

Prefer standards and maintained documentation over isolated snippets. Record what you learned in your own words. Rebuild earlier projects with new knowledge instead of endlessly collecting tutorials.

## Final challenge

Create a second tiny site without looking at the capstone source. Limit yourself to 60 minutes. Afterwards compare:

- Setup speed.
- Structural correctness.
- Semantic choices.
- Number and type of mistakes.
- Ability to explain decisions.

The comparison measures transferable skill rather than memory of one project.

**C20-Q1 - Boundary decision.** A capstone needs authenticated accounts, permanent form storage, and email confirmation. Which parts can HTML describe, and which require server or managed-service capabilities?

## Common misconceptions

- Finishing HTML does not mean memorizing every element.
- A visually plain capstone can still demonstrate excellent document engineering.
- Validation is necessary evidence, but a valid page can still contain unclear or inaccessible content.
- JavaScript is not required to prove HTML mastery.
- Publishing a site does not automatically make it secure, private, fast, or maintainable.
- A low rubric category identifies the next skill to practice; it does not erase completed learning.

## Chapter summary

The capstone combines planning, semantic structure, navigation, media, data, forms, accessibility, and systematic testing. Completion means that you can build and defend a coherent HTML site, recognize the limits of HTML, and select an appropriate next layer without abandoning the document fundamentals beneath it.

## Mastery checklist

### Graduation checklist

- [ ] My capstone has a clear audience and goal.
- [ ] Every page has complete metadata and semantic regions.
- [ ] Navigation and paths work from every page.
- [ ] Text, lists, media, tables, and forms use justified semantics.
- [ ] The site works with keyboard and zoom.
- [ ] I validated, tested, recorded, repaired, and retested.
- [ ] I can defend my decisions.
- [ ] I know my next learning sequence.
- [ ] I can identify performance, privacy, compatibility, and server-boundary risks.

## Closing perspective

HTML rewards careful thinking. A strong author respects content, users, tools, and the document model. The code may be shorter than a program, but its decisions affect every later layer of a website.

Return to the [course home](../HTML_CRASH_COURSE.md), complete any unchecked mastery items, and keep building.

Solutions for deterministic review questions: [Advanced and integration answer key](../answer-keys/05-advanced-html-and-debugging.md#chapter-20)

## Authoritative references

- [WHATWG HTML Living Standard](https://html.spec.whatwg.org/multipage/)
- [W3C WAI: Accessibility principles](https://www.w3.org/WAI/fundamentals/accessibility-principles/)
- [W3C WAI: Evaluating accessibility](https://www.w3.org/WAI/test-evaluate/)
