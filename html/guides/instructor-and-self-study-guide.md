# Instructor and Self-study Guide

[Course home](../HTML_CRASH_COURSE.md)

## Teaching philosophy

This book uses a spiral progression. New chapters introduce one central idea and deliberately reuse earlier skills. Students move through:

```text
recognize -> explain -> reproduce -> modify -> debug -> design -> defend
```

Correct output is not enough. Students should explain why an element fits, how a path resolves, and what evidence verifies behavior.

## Recommended lesson structure

For a 60-90 minute class:

1. Retrieval warm-up - 5-10 minutes.
2. Instructor model - 10-15 minutes.
3. Guided coding - 15-20 minutes.
4. Independent challenge - 15-25 minutes.
5. Peer explanation or debugging - 10 minutes.
6. Exit check - 5 minutes.

Avoid live-coding long flawless pages. Small examples and intentional mistakes make reasoning observable.

## Questioning strategies

Ask:

- What does this content mean?
- Which element communicates that meaning?
- What is the current file's directory?
- What tree relationship does this markup create?
- What do you predict before refreshing?
- What evidence supports the diagnosis?
- Can a keyboard user operate it?
- What belongs to a later layer?
- What performance, privacy, or compatibility evidence supports this decision?

Replace “Does everyone understand?” with a concrete retrieval prompt.

## Assessment model

Use three forms of evidence:

- **Knowledge**: terminology, syntax, and explanation.
- **Performance**: building and debugging.
- **Product**: projects evaluated with rubrics.

Suggested weighting:

| Evidence | Weight |
| --- | ---: |
| Chapter practice and retrieval | 20% |
| Checkpoint practicals | 25% |
| Projects 1-3 | 25% |
| Capstone and defense | 30% |

For self-study, use the same categories as a diagnostic rather than a grade.

Use the [entry diagnostic and final assessment](../assessments/course-assessments.md) when formal evidence is useful. The entry diagnostic must not be used to exclude beginners; it chooses a pace and identifies concepts needing demonstration. The final combines written reasoning, source repair, construction, test evidence, and defense so that a polished artifact cannot conceal misunderstanding.

For consistent scoring:

1. Review the criterion before reviewing student identity or prior performance when practical.
2. Cite the exact file, source, behavior, or explanation supporting each major deduction.
3. Accept equivalent conforming solutions rather than one memorized formatting style.
4. Require repair of critical accessibility barriers even when the numerical score passes.
5. Use fresh but equivalent content for reassessment.

## Giving feedback

Prioritize:

1. Broken structure or inaccessible interaction.
2. Semantic misunderstanding.
3. Missing content relationships.
4. Maintainability.
5. Formatting conventions.

Give evidence and a question:

> The label's `for` is `email`, but the input ID is `student-email`. Which value must match to create the relationship?

Do not rewrite the entire project for the student. Require a repair and retest.

## Pair and group activities

- One student draws a directory tree; another calculates paths.
- One describes intended content; another selects semantics.
- One inserts three bugs; another writes a defect report and repairs them.
- Students compare alt text for the same image in different contexts.
- Students perform keyboard reviews of each other's forms.

Peer review must remain respectful and evidence-based.

## Accommodations and inclusive teaching

- Provide text instructions as well as spoken instructions.
- Allow keyboard-only and assistive-technology workflows.
- Avoid timed typing as the main measure of knowledge.
- Supply downloadable examples when visual copying creates a barrier.
- Permit different project topics while keeping equivalent criteria.
- Explain idioms and technical vocabulary.
- Protect personal privacy; never require public biographical disclosure.
- Treat chapter study times as planning ranges, not speed requirements or grading limits.

## Academic integrity and AI tools

Students may use references and, when course policy allows, AI assistance. Require them to:

- Identify external help.
- Verify generated markup.
- Explain every submitted element and attribute.
- Preserve no secrets or personal data in prompts.
- Complete an oral, written, or debugging defense.

Unexplained working code is incomplete evidence of learning.

## Intervention points

If a student struggles with:

- **Files**: return to Chapter 2 and physically trace paths.
- **Nesting**: use boxes or a drawn tree from Chapter 4.
- **Semantics**: separate meaning from appearance using Chapter 5.
- **Forms**: trace accessible name and submitted name separately.
- **Debugging**: require one symptom, one hypothesis, one change.
- **Modern features**: require a standards source, compatibility expectation, fallback, and dated test.

## Completion standard

A successful student can build a small site from a written brief, explain its structure, operate it with a keyboard, diagnose common failures, review performance/privacy/compatibility risks, and identify which desired improvements belong to CSS, JavaScript, or server development.
