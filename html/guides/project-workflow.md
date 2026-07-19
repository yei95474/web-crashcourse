# Project Workflow

[Course home](../HTML_CRASH_COURSE.md) | [Project rubrics](../reference/project-rubrics.md) | [Content rights and attribution](content-rights-and-attribution.md)

This workflow scales from a one-page exercise to the capstone.

## 1. Define

Write:

- Audience.
- User goal.
- Site purpose.
- Required pages.
- Required content and evidence.
- Constraints.
- Definition of done.

Example:

> Create a three-page HTML site that helps new club members understand activities and submit a local demonstration registration form.

## 2. Inventory content

List content before files or visual layout. Separate:

- Site-wide content.
- Page-specific content.
- Structured data.
- Media.
- User input.
- Downloads and external resources.

Delete content that serves no user need. Identify missing facts rather than filling pages with placeholder prose.

For every external asset, record its creator or owner, source, permission or license, required attribution, modifications, privacy/consent status, and accessibility work. Use the [content-rights guide](content-rights-and-attribution.md) and replace anything whose publication basis is uncertain.

## 3. Design information architecture

Group content into pages with one clear purpose each. Draw:

- Site map.
- Directory tree.
- Navigation labels and destinations.
- Major page sections.

Prefer the shallowest structure that remains meaningful.

## 4. Specify pages

For each page record:

| Field | Decision |
| --- | --- |
| Filename | Lowercase, descriptive, hyphenated |
| Title | Unique page topic plus site |
| `h1` | Visible main topic |
| Purpose | User question answered |
| Sections | Logical heading outline |
| Media | Purpose and alternative |
| Data | List, table, or prose |
| Interaction | Link, form, or native control |
| Data/privacy | Field purpose, necessity, third parties |
| Performance | Media size, dimensions, loading decision |
| Compatibility | Required features and supported environments |
| Tests | Observable expected results |

## 5. Build the structural shell

Create complete skeletons, metadata, landmarks, headings, navigation, and footers. Mark the current page. Validate and test all navigation before adding detail.

## 6. Add content in slices

Complete one page or user path at a time:

1. Text semantics.
2. Links and lists.
3. Media.
4. Tables if justified.
5. Forms and constraints.
6. Native interaction if justified.
7. Validation and accessibility review.

Keep the site working after every slice.

## 7. Test continuously

Maintain a test table:

| ID | Page | Action/input | Expected | Actual | Status |
| --- | --- | --- | --- | --- | --- |
| NAV-01 | Contact | Activate Home | Home opens | | |

Cover happy paths, boundary cases, invalid inputs, missing media, keyboard use, zoom, and nested-page paths.

Also record large resources, third-party requests, personal-data fields, and any modern feature whose support is required.

## 8. Review content and semantics

Read the page without thinking about appearance:

- Does the purpose become clear from title, `h1`, and introduction?
- Does heading order reveal a coherent outline?
- Can every link destination be predicted?
- Are lists and tables genuine relationships?
- Are instructions complete without images or color?
- Does every external asset have a defensible source, permission or license, attribution, and accessibility alternative?

## 9. Audit and repair

Use the [debugging checklist](debugging-checklist.md), validate every page, and apply the appropriate rubric. Record defects. Retest after repair.

## 10. Reflect

Write:

- Strongest decision.
- Hardest defect and its cause.
- One accessibility improvement.
- One remaining limitation.
- Next technical layer required.
- One resource or data field that could be removed without harming the user goal.

Reflection converts a completed artifact into transferable knowledge.
