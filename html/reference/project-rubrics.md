# Project Rubrics

[Course home](../HTML_CRASH_COURSE.md)

## Scoring scale

| Score | Description |
| ---: | --- |
| 4 | Complete, correct, deliberate, and independently explained |
| 3 | Functional with minor errors or incomplete explanation |
| 2 | Partially functional; important misunderstanding remains |
| 1 | Minimal attempt or copied pattern without understanding |
| 0 | Missing or unrelated |

Multiply category scores by weights where shown. Accessibility failures that prevent use should be repaired even if the numerical score appears acceptable.

## Project 1: About Me page

| Category | Weight | Evidence |
| --- | ---: | --- |
| Document skeleton | 2 | Doctype, language, charset, viewport, title, head/body |
| Text semantics | 3 | Logical headings, paragraphs, emphasis, specialized text |
| Syntax quality | 2 | Correct nesting, attributes, indentation |
| Content clarity | 2 | Useful, respectful, coherent content |
| Explanation | 1 | Student can defend element choices |

Maximum weighted points: 40.

Do not require students to disclose private biographical information. A fictional persona is acceptable.

## Project 2: Recipe or hobby site

| Category | Weight | Evidence |
| --- | ---: | --- |
| Multi-page navigation | 3 | Consistent links, correct paths, current-page state |
| Lists and organization | 2 | List type matches relationship; valid nesting |
| Images | 3 | Portable paths, purpose-based alt, figure/caption |
| Semantic structure | 3 | Useful landmarks and headings |
| Metadata and source quality | 2 | Unique titles, readable source, documented rights/attribution for external content |
| Testing | 2 | Every link and resource tested from every page |

Maximum weighted points: 60.

## Project 3: Event-registration page

| Category | Weight | Evidence |
| --- | ---: | --- |
| Event content and structure | 2 | Clear purpose, headings, landmarks |
| Schedule table | 3 | Genuine data, caption, row/column headers |
| Form controls | 4 | Labels, names, groups, values, suitable types |
| Validation and minimal data | 3 | Justified constraints, visible instructions, only necessary fields |
| Accessibility | 4 | Keyboard use, names, grouping, no sensory-only information |
| Limitations notice | 1 | Explains that local HTML does not store submissions |
| Testing | 3 | Invalid, boundary, valid, and keyboard cases |

Maximum weighted points: 80.

## Project 4: Capstone website

| Category | Weight | Evidence |
| --- | ---: | --- |
| Purpose and information architecture | 3 | Brief, content inventory, site map, page responsibilities |
| Document foundations | 3 | Complete metadata and valid skeletons |
| Semantic content | 4 | Headings, regions, text, lists, appropriate advanced semantics |
| Navigation and paths | 4 | Consistent site-wide navigation and verified resources |
| Media and performance | 3 | Suitable files, dimensions/loading decisions, alternatives, captions, fallbacks |
| Tables/forms/data/interaction | 4 | Justified, labeled, keyboard-operable structures; minimal personal data |
| Accessibility | 5 | Manual audit evidence and repairs |
| Validation, compatibility, and testing | 4 | Validator, feature support, browsers, zoom, links, inputs, defect records |
| Maintainability and third parties | 2 | Naming, consistency, no obsolete markup, justified embeds/resources, documented rights/attribution |
| Defense and reflection | 3 | Decisions, limitations, next steps explained independently |

Maximum weighted points: 140.

### Capstone performance bands

| Percentage | Interpretation |
| ---: | --- |
| 90-100% | Ready to continue confidently into CSS and JavaScript |
| 75-89% | Strong foundation; repair identified weak categories |
| 60-74% | Partial foundation; revisit chapters linked to low scores |
| Below 60% | Rebuild a smaller project with guided feedback |

A percentage is diagnostic, not a statement about personal ability.

### Required cross-cutting capstone evidence

- Resource inventory identifying large media, loading decisions, and third-party requests.
- Form-field inventory stating the purpose and necessity of personal data.
- Compatibility note for modern features required by the project.
- Privacy and fallback review for embeds or external services.
- Content ledger recording ownership/source, permission or license, modifications, attribution, consent, and accessibility work.

These requirements are evaluated through the existing categories rather than adding extra points.

## Reviewer comment format

Use evidence, impact, and next action:

```text
Evidence: register.html has three radio buttons with different name values.
Impact: Users can select all three although the question requests one choice.
Next action: Give the radio buttons one shared name, then retest with arrow keys.
```

## Self-assessment questions

- Can I explain this pattern without reading it?
- Did I test from nested pages and not only the homepage?
- What user is blocked by the highest-priority defect?
- Which improvement belongs to HTML, CSS, JavaScript, or a server?
- What evidence proves the repair worked?
