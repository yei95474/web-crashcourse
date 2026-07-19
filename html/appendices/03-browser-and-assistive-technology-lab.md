# Appendix 3: Browser and Assistive-technology Lab

[Course home](../HTML_CRASH_COURSE.md) | [Previous appendix](02-less-common-html-and-platform-boundaries.md)

## Status of this appendix

This optional lab introduces evidence-gathering tools. Completing it does not certify a website as accessible or replace testing by people with disabilities. Screen readers are sophisticated applications; this is an orientation, not full training.

## Learning objectives

You will learn to:

- Compare a local file with a page served over local HTTP.
- Inspect source, DOM, network requests, and the accessibility tree.
- Perform keyboard-only, zoom, and basic screen-reader checks.
- Record expected and actual results.
- Avoid drawing conclusions from one tool or browser.

## A3.1 Tool map

Different tools answer different questions:

| Tool or view | Best question |
| --- | --- |
| Code editor | What source did I save? |
| View Source | What source was loaded? |
| Elements/Inspector | What document tree did the browser parse? |
| Network panel | Which resources were requested and returned? |
| Console | What runtime, policy, or loading messages occurred? |
| Accessibility tree | What names, roles, states, and relationships are exposed? |
| Keyboard test | Can a non-pointer user reach and operate it? |
| Screen reader | How is the interface presented through speech or braille semantics? |
| Validator | Does markup conform to authoring rules? |

No single row answers every question.

## A3.2 Common browser shortcuts

Shortcuts vary by browser, operating system, keyboard layout, and settings.

| Action | Windows/Linux common shortcut | macOS common shortcut |
| --- | --- | --- |
| Developer Tools | `F12` or `Ctrl+Shift+I` | `Command+Option+I` |
| View Source | `Ctrl+U` | `Command+Option+U` in many browsers |
| Reload | `Ctrl+R` | `Command+R` |
| Hard reload tools | Browser-specific | Browser-specific |
| Address bar | `Ctrl+L` | `Command+L` |
| Find in page | `Ctrl+F` | `Command+F` |
| Zoom in | `Ctrl++` | `Command++` |
| Zoom out | `Ctrl+-` | `Command+-` |
| Reset zoom | `Ctrl+0` | `Command+0` |

Use browser menus when a shortcut differs. The objective is inspection, not shortcut memorization.

## A3.3 Safe editor extensions

An editor extension executes software with access determined by the editor and operating system. Before installation:

- Confirm the publisher and marketplace source.
- Review permissions, maintenance activity, and recent reports.
- Prefer widely used, narrowly scoped tools.
- Remove extensions you no longer need.
- Do not install an extension merely because a tutorial demands it.

Live preview is convenient, not required to learn HTML.

## A3.4 Local file versus local HTTP

Opening `index.html` directly commonly produces:

```text
file:///C:/projects/site/index.html
```

A local server may produce:

```text
http://127.0.0.1:5500/index.html
```

The HTML can be identical, but the environments differ:

- HTTP responses have status codes and headers.
- Servers associate resources with media or MIME types.
- Directory index behavior can apply.
- Origin-based security rules differ.
- Some JavaScript requests and module behavior are restricted under `file:`.
- Root-relative paths resolve against the server origin rather than a local project concept.

Do not publish a development server to an untrusted network. Bind it locally unless you deliberately need device testing and understand firewall exposure.

## A3.5 Local-server comparison lab

1. Open one project through `file:///`.
2. Record its address and whether navigation, images, and forms behave.
3. Open the same project through a trusted local server.
4. Record the HTTP address.
5. Open the Network panel and reload.
6. Identify the document request, status, and content type.
7. Misspell one image path and observe the failed request.
8. Restore the path and retest.
9. Explain which evidence was unavailable or different under direct file loading.

Do not leave the intentional defect in the project.

## A3.6 Keyboard-only lab

Without touching the mouse:

1. Start at the address bar or beginning of the document.
2. Use `Tab` and `Shift+Tab` through all interactive elements.
3. Activate links with `Enter`.
4. Activate buttons with `Enter` and `Space`.
5. Toggle checkboxes with `Space`.
6. Navigate a radio group with arrow keys.
7. Open and close each disclosure or dialog.
8. Confirm focus is always visible.
9. Confirm focus order follows reading and task order.
10. Confirm no component traps focus.

Record any element that is unreachable, unnamed, unexpectedly ordered, or impossible to close.

## A3.7 Accessibility-tree inspection

Browser tools commonly expose an accessibility panel or accessibility properties inside the element inspector.

Inspect:

- The page `title`.
- Document language.
- Main heading and subheadings.
- Landmarks such as navigation and main.
- One descriptive link.
- One informative image.
- One decorative image.
- A table header and data cell.
- A labeled input.
- A radio group.
- A details disclosure.

For each, predict the name, role, state, and relevant relationships before inspecting. A mismatch between prediction and evidence indicates either a markup problem or a gap in your mental model.

## A3.8 Screen-reader orientation

Common choices include:

- **Narrator**, built into Windows.
- **NVDA**, a free Windows screen reader.
- **VoiceOver**, built into macOS and Apple mobile devices.
- **TalkBack**, commonly available on Android.

Only enable a screen reader when you know how to exit it. Consult its current official command guide because keyboard commands and modes vary.

Useful first tasks:

1. Read continuously from the top.
2. Move by heading.
3. List or navigate landmarks.
4. Move through links.
5. Enter and complete a form.
6. Inspect an image announcement.
7. Navigate a data table.
8. Expand a disclosure and detect its state.

Do not judge the screen reader's voice speed or unfamiliar interaction as a website defect. Compare what it announces with the semantics you intended.

### Starting and stopping examples

- Windows Narrator commonly toggles with `Windows+Ctrl+Enter`.
- VoiceOver on macOS commonly toggles with `Command+F5` or Touch ID pressed three times on supported keyboards.
- NVDA should be started and exited using its installed shortcuts and current user guide.

Verify commands in current operating-system documentation before teaching them.

## A3.9 Zoom and reflow

At 200% browser zoom:

- Text should remain readable.
- Controls should not overlap.
- Content should not be clipped.
- Horizontal scrolling should not be required for ordinary text.
- Tables and large media should remain understandable.
- Focused elements should remain visible.

Many visual failures require CSS repairs, but HTML structure and media dimensions can still contribute. Record the correct layer for each repair.

## A3.10 Compatibility research workflow

When a feature is unfamiliar:

1. Read its current definition in the HTML Living Standard.
2. Read a maintained developer reference.
3. Check browser-compatibility data.
4. Identify the minimum browsers and assistive technologies your project supports.
5. Build a small isolated test.
6. Test the unsupported or failure state.
7. Decide whether the feature is required, enhanced, or unsuitable.
8. Record the date and sources.

Compatibility tables do not replace testing, and one successful test does not prove universal support.

## A3.11 Test record

```text
Test ID:
Date:
Page/version:
Browser and version:
Operating system:
Assistive technology:
Setup:
Action:
Expected:
Actual:
Result:
Evidence:
Repair:
Retest:
Remaining limitation:
```

Avoid including personal user data in screenshots or records.

## A3.12 Mini audit scenario

Audit the event-registration project:

1. Validate every page.
2. Compare local-file and local-server behavior.
3. Inspect the document and accessibility trees.
4. Complete the form by keyboard.
5. Try 200% zoom.
6. Perform a basic screen-reader pass.
7. Test in a second browser engine.
8. Record at least three successful tests and every defect found.
9. Repair the highest-impact defect.
10. Retest the original steps.

## Common misconceptions

- Developer Tools shows parsed state, not necessarily saved source.
- Passing one automated scan does not prove accessibility.
- A screen-reader test by a sighted beginner does not replace disabled-user research.
- Keyboard focusability does not guarantee complete operation.
- `file:///` and HTTP environments are not identical.
- Browser-support data is evidence, not a guarantee.
- Testing is incomplete until repaired behavior is retested.

## Authoritative references

- [W3C WAI: Evaluating Web Accessibility](https://www.w3.org/WAI/test-evaluate/)
- [W3C WAI: Easy Checks](https://www.w3.org/WAI/test-evaluate/preliminary/)
- [Microsoft: Complete guide to Narrator](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1)
- [NV Access: NVDA User Guide](https://download.nvaccess.org/documentation/userGuide.html)
- [Apple: VoiceOver User Guide](https://support.apple.com/guide/voiceover/welcome/mac)

Return to the [course home](../HTML_CRASH_COURSE.md) or use the [topic index](../reference/topic-index.md).
