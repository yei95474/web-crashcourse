# Further Reading

[Course home](../HTML_CRASH_COURSE.md)

Use maintained references to verify unfamiliar details. Documentation is a professional tool, not a sign of weakness.

## Primary specification

- [WHATWG HTML Living Standard](https://html.spec.whatwg.org/multipage/) - normative, comprehensive, and technical.
- [HTML Standard for Web Developers](https://html.spec.whatwg.org/dev/) - developer-oriented view of the living standard.

Read the specification when exact conformance, content models, parsing, or API behavior matters. It is a reference, not the best first tutorial.

## Standards and compatibility literacy

- [WHATWG FAQ](https://whatwg.org/faq)
- [MDN: Web standards curriculum](https://developer.mozilla.org/en-US/curriculum/core/web-standards/)
- [Web Platform Tests](https://web-platform-tests.org/)

Distinguish defined behavior, browser implementation, compatibility summaries, and your own dated test evidence.

## Learning and element references

- [MDN: Structuring content with HTML](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content)
- [MDN: HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements)
- [MDN: HTML attribute reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes)
- [MDN: HTTP overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview)

For unfamiliar features, inspect semantics, syntax, examples, accessibility notes, and browser compatibility rather than copying only the first code block.

## Accessibility

- [W3C Web Accessibility Initiative tutorials](https://www.w3.org/WAI/tutorials/)
- [W3C: Introduction to Web Accessibility](https://www.w3.org/WAI/fundamentals/accessibility-intro/)
- [Web Content Accessibility Guidelines overview](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/)

Use the ARIA guide when building advanced scripted widgets, after confirming that native HTML cannot meet the need.

## Forms

- [WHATWG: Forms](https://html.spec.whatwg.org/multipage/forms.html)
- [WHATWG: Input types and attributes](https://html.spec.whatwg.org/multipage/input.html)
- [W3C WAI: Forms tutorial](https://www.w3.org/WAI/tutorials/forms/)

Read the form standard when deciding among `type`, `autocomplete`, and `inputmode`; they describe different aspects of one field.

## International text

- [W3C Internationalization: Authoring HTML](https://www.w3.org/International/techniques/authoring-html)
- [WHATWG: Text-level semantics](https://html.spec.whatwg.org/multipage/text-level-semantics.html)
- [WHATWG: The `dir` attribute](https://html.spec.whatwg.org/multipage/dom.html#the-dir-attribute)

Test language and direction with real content rather than placeholder characters.

## Performance, privacy, and security

- [WHATWG: Lazy-loading attributes](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#lazy-loading-attributes)
- [WHATWG: Fetch-priority attributes](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#fetch-priority-attributes)
- [W3C: Subresource Integrity](https://www.w3.org/TR/SRI/)
- [W3C: Content Security Policy Level 3](https://www.w3.org/TR/CSP3/)
- [W3C WAI: Forms tutorial](https://www.w3.org/WAI/tutorials/forms/)

Treat performance hints as measured optimizations and CSP/SRI as parts of broader deployment and security processes.

## Less-common platform features

- [WHATWG: Image maps](https://html.spec.whatwg.org/multipage/image-maps.html)
- [WHATWG: Canvas](https://html.spec.whatwg.org/multipage/canvas.html)
- [WHATWG: Scripting elements](https://html.spec.whatwg.org/multipage/scripting.html)
- [WHATWG: Microdata](https://html.spec.whatwg.org/multipage/microdata.html)

These are recognition references. Do not add a feature merely to demonstrate that it exists.

## Browser and assistive-technology testing

- [W3C WAI: Evaluating Web Accessibility](https://www.w3.org/WAI/test-evaluate/)
- [Microsoft Narrator guide](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1)
- [NVDA User Guide](https://download.nvaccess.org/documentation/userGuide.html)
- [Apple VoiceOver User Guide](https://support.apple.com/guide/voiceover/welcome/mac)

Record browser, operating system, assistive technology, version, setup, and expected result when reporting compatibility.

## Validation and testing

- [Nu HTML Checker](https://validator.w3.org/nu/)
- [W3C WAI: Evaluating Web Accessibility Overview](https://www.w3.org/WAI/test-evaluate/)
- Browser Developer Tools documentation for your chosen browser.

Never upload confidential source or private data to a public validation service.

## Content rights and accessible media

- [Creative Commons: About CC Licenses](https://creativecommons.org/share-your-work/cclicenses/)
- [Creative Commons: License Your Work](https://creativecommons.org/cc-license-your-work/)
- [W3C WAI: Making Audio and Video Media Accessible](https://www.w3.org/WAI/media/av/)

Read the exact license and preserve a source record. Permission to reuse material and the work required to make it accessible are separate responsibilities.

## How to judge a source

Ask:

1. Is it the current standard, an official project, or a maintained expert reference?
2. Is the page dated or versioned?
3. Does it explain semantics and accessibility?
4. Does it distinguish current, experimental, deprecated, and obsolete behavior?
5. Can you confirm a surprising claim in a second authoritative source?
6. Does the example solve the same problem you have?

Forum posts and videos can reveal useful experiences, but verify technical rules through current documentation.

## Suggested next curricula

After the capstone, continue with maintained courses covering:

- CSS fundamentals and layout.
- JavaScript fundamentals and DOM interaction.
- Git and version control.
- Web performance.
- HTTP and server development.
- Accessibility testing.

Keep this HTML book nearby. Every later layer still depends on the document.
