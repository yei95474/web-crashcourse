# Edition History and Errata

[Course home](../HTML_CRASH_COURSE.md) | [Further reading](further-reading.md)

## Current release

- **Book**: HTML Crash Course, Second Edition
- **Release**: 2.1
- **Release date**: 2026-07-14
- **Technical review baseline**: [WHATWG HTML Living Standard](https://html.spec.whatwg.org/multipage/), [MDN curriculum](https://developer.mozilla.org/en-US/curriculum/), and [W3C WAI guidance](https://www.w3.org/WAI/tutorials/) available on 2026-07-14
- **Format**: plain Markdown

The date records when the manuscript's standards links, feature cautions, internal navigation, and deterministic exercises were last systematically reviewed. It is not a guarantee that every browser released later behaves identically.

## Feature-status labels

Use these interpretations throughout the book:

- **Core**: durable knowledge expected in the required beginner path.
- **Advanced**: useful after the foundations and likely to require additional testing or context.
- **Recognition only**: learners should identify the feature and know where its responsibility belongs, not implement it from memory.
- **Check compatibility**: verify current support in the browsers and assistive technologies selected for the project.
- **Platform boundary**: HTML exposes or references the feature, but reliable implementation also needs CSS, JavaScript, server configuration, build tooling, or deployment control.

Absence of a warning does not remove the duty to test a production project.

## Release history

### Release 2.1 — 2026-07-14

- Added explicit key vocabulary and suggested study times to every core chapter.
- Added an entry diagnostic, final written assessment, practical examinations, defense, scoring guidance, and outcome-evidence matrix.
- Added standards-literacy, standards-mode, browser-default, alternate-language metadata, form-hint, form-owner, error-summary, inertness, find-in-page, and shortcut-caution material.
- Added content-rights, licensing, attribution, consent, and student-privacy guidance.
- Added a documented maintenance and errata process.

### Second-edition baseline — date not recorded

- Expanded the original crash course into 20 core chapters.
- Added answer keys, projects, rubrics, guides, references, and three optional appendices.
- Added second-edition material on forms, international text, performance, privacy, security, advanced tables, browser testing, and platform boundaries.

## Reporting an erratum

Record enough evidence for another person to reproduce the issue:

```text
File:
Heading or exercise ID:
Current wording or code:
Why it is wrong or unclear:
Proposed correction:
Authoritative source, if technical:
Browser/OS/assistive technology and version, if behavioral:
Date observed:
```

Classify the report as one of:

- Technical correctness
- Accessibility
- Broken link or anchor
- Exercise/answer mismatch
- Ambiguous explanation
- Typographical or formatting error
- Browser-compatibility change

For a rapidly changing feature, prefer a dated compatibility note over a timeless claim such as “all browsers support this.”

## Maintenance checklist

Before publishing a new release:

1. Review the HTML Living Standard and official learning references for material changes.
2. Recheck advanced-feature compatibility notes.
3. Resolve every relative file link and heading anchor.
4. Confirm one top-level heading and paired code fences in every Markdown file.
5. Check UTF-8 decoding and search for replacement or mojibake characters.
6. Confirm unique exercise IDs and complete answer-key coverage.
7. Revalidate representative HTML examples.
8. Review accessibility examples with current WAI guidance.
9. Recheck external references and replace moved or obsolete links.
10. Record the release date and a concise change summary here.

## Known scope boundaries

This edition does not attempt to teach CSS, JavaScript, ARIA widget engineering, backend development, Git, deployment operations, legal compliance, or exhaustive browser internals. It prepares students to identify those boundaries and continue into dedicated courses.
