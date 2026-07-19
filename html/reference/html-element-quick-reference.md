# HTML Element Quick Reference

[Course home](../HTML_CRASH_COURSE.md) | [Topic index](topic-index.md)

This is a reminder, not a substitute for learning context or consulting the current standard. “Recognition” marks optional material outside the required core.

## Document and metadata

| Element | Purpose | Learn |
| --- | --- | --- |
| `html` | Document root and default language | [Chapter 3](../chapters/03-your-first-html-document.md) |
| `head` | Document metadata container | [Chapters 3 and 14](../chapters/14-document-head-and-metadata.md) |
| `body` | Presented document content | [Chapter 3](../chapters/03-your-first-html-document.md) |
| `title` | Browser/interface page title | [Chapter 14](../chapters/14-document-head-and-metadata.md#142-page-titles) |
| `meta` | Metadata such as charset, description, viewport, or robots | [Chapter 14](../chapters/14-document-head-and-metadata.md) |
| `link` | Relationship to an external resource | [Chapter 14](../chapters/14-document-head-and-metadata.md) |
| `base` | Base URL or target for relative URLs | [Appendix 2, recognition](../appendices/02-less-common-html-and-platform-boundaries.md#a21-the-base-element) |
| `style` | Embedded CSS rules | [Chapter 20 transition](../chapters/20-capstone-and-next-steps.md#208-next-css) |
| `script` | Script data or an external script | [Chapter 14](../chapters/14-document-head-and-metadata.md#146-linking-css-and-javascript) |
| `noscript` | Content for disabled or unsupported scripting | [Appendix 2, recognition](../appendices/02-less-common-html-and-platform-boundaries.md#a27-noscript) |

## Page structure

| Element | Purpose | Learn |
| --- | --- | --- |
| `header` | Introductory content for a page or section | [Chapter 10](../chapters/10-semantic-page-structure.md#102-major-elements) |
| `nav` | Major navigation | [Chapters 6 and 10](../chapters/06-links-paths-and-navigation.md#68-navigation-landmarks) |
| `main` | Unique central page content | [Chapter 10](../chapters/10-semantic-page-structure.md) |
| `search` | Search or filtering region | [Chapter 10](../chapters/10-semantic-page-structure.md) |
| `article` | Independently meaningful content | [Chapter 10](../chapters/10-semantic-page-structure.md) |
| `section` | Thematic subdivision | [Chapter 10](../chapters/10-semantic-page-structure.md) |
| `aside` | Indirectly related content | [Chapter 10](../chapters/10-semantic-page-structure.md) |
| `footer` | Footer for a page or section | [Chapter 10](../chapters/10-semantic-page-structure.md) |
| `address` | Contact information for the nearest article or document | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `div` | Generic block container | [Chapter 7](../chapters/07-lists-and-content-grouping.md#75-generic-containers-div-and-span) |

## Text

| Element | Purpose | Learn |
| --- | --- | --- |
| `h1`–`h6` | Heading levels | [Chapter 5](../chapters/05-text-content-and-semantics.md#52-headings-form-an-outline) |
| `p` | Paragraph | [Chapter 5](../chapters/05-text-content-and-semantics.md#53-paragraphs-and-line-breaks) |
| `strong` | Strong importance, urgency, or seriousness | [Chapter 5](../chapters/05-text-content-and-semantics.md#54-importance-emphasis-and-visual-convention) |
| `em` | Stress emphasis | [Chapter 5](../chapters/05-text-content-and-semantics.md#54-importance-emphasis-and-visual-convention) |
| `b` | Attention without added importance | [Chapter 5](../chapters/05-text-content-and-semantics.md#54-importance-emphasis-and-visual-convention) |
| `i` | Alternate voice or conventional offset | [Chapter 5](../chapters/05-text-content-and-semantics.md#54-importance-emphasis-and-visual-convention) |
| `small` | Side comments or fine print | [Chapter 5](../chapters/05-text-content-and-semantics.md#57-specialized-text-semantics) |
| `mark` | Contextually relevant highlight | [Chapter 5](../chapters/05-text-content-and-semantics.md#57-specialized-text-semantics) |
| `blockquote` | Block quotation | [Chapter 5](../chapters/05-text-content-and-semantics.md#55-quotations-and-citations) |
| `q` | Inline quotation | [Chapter 5](../chapters/05-text-content-and-semantics.md#55-quotations-and-citations) |
| `cite` | Title of a work | [Chapter 5](../chapters/05-text-content-and-semantics.md#55-quotations-and-citations) |
| `code` | Computer code | [Chapter 5](../chapters/05-text-content-and-semantics.md#56-code-and-exact-text) |
| `pre` | Preformatted text | [Chapter 5](../chapters/05-text-content-and-semantics.md#56-code-and-exact-text) |
| `kbd` | User input | [Chapter 5](../chapters/05-text-content-and-semantics.md#56-code-and-exact-text) |
| `samp` | Program output | [Chapter 5](../chapters/05-text-content-and-semantics.md#56-code-and-exact-text) |
| `var` | Variable | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `dfn` | Defining occurrence of a term | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `data` | Visible text paired with machine-readable value | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `abbr` | Abbreviation | [Chapter 5](../chapters/05-text-content-and-semantics.md#57-specialized-text-semantics) |
| `time` | Machine-readable date or time | [Chapter 5](../chapters/05-text-content-and-semantics.md#57-specialized-text-semantics) |
| `sub`, `sup` | Subscript and superscript | [Chapter 5](../chapters/05-text-content-and-semantics.md#57-specialized-text-semantics) |
| `ins`, `del` | Inserted and deleted content | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `ruby`, `rt`, `rp` | Ruby base and annotations | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `bdi`, `bdo` | Bidirectional isolation and override | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#175-directionality) |
| `wbr` | Optional word-break opportunity | [Chapter 5](../chapters/05-text-content-and-semantics.md#58-editorial-and-language-aware-text) |
| `br` | Meaningful line break | [Chapter 5](../chapters/05-text-content-and-semantics.md#53-paragraphs-and-line-breaks) |
| `hr` | Thematic break | [Chapter 5](../chapters/05-text-content-and-semantics.md#53-paragraphs-and-line-breaks) |
| `span` | Generic inline container | [Chapter 7](../chapters/07-lists-and-content-grouping.md#75-generic-containers-div-and-span) |

## Links and lists

| Element | Purpose | Learn |
| --- | --- | --- |
| `a` | Hyperlink | [Chapter 6](../chapters/06-links-paths-and-navigation.md) |
| `ul` | Unordered list | [Chapter 7](../chapters/07-lists-and-content-grouping.md#71-lists-express-relationships) |
| `ol` | Ordered list | [Chapter 7](../chapters/07-lists-and-content-grouping.md#71-lists-express-relationships) |
| `li` | List item | [Chapter 7](../chapters/07-lists-and-content-grouping.md) |
| `dl` | Description or name-value list | [Chapter 7](../chapters/07-lists-and-content-grouping.md#71-lists-express-relationships) |
| `dt` | Term or name | [Chapter 7](../chapters/07-lists-and-content-grouping.md#71-lists-express-relationships) |
| `dd` | Description or value | [Chapter 7](../chapters/07-lists-and-content-grouping.md#71-lists-express-relationships) |

## Media and embedding

| Element | Purpose | Learn |
| --- | --- | --- |
| `img` | Image with intentional alternative | [Chapter 8](../chapters/08-images-figures-and-responsive-media.md) |
| `figure` | Self-contained referenced content | [Chapter 8](../chapters/08-images-figures-and-responsive-media.md#83-figures-and-captions) |
| `figcaption` | Visible figure caption | [Chapter 8](../chapters/08-images-figures-and-responsive-media.md#83-figures-and-captions) |
| `picture` | Image-candidate wrapper | [Chapter 8](../chapters/08-images-figures-and-responsive-media.md#86-art-direction-with-picture) |
| `source` | Alternate image, audio, or video source | [Chapters 8 and 9](../chapters/09-audio-video-and-embedded-content.md) |
| `audio` | Native audio player | [Chapter 9](../chapters/09-audio-video-and-embedded-content.md#91-native-media-players) |
| `video` | Native video player | [Chapter 9](../chapters/09-audio-video-and-embedded-content.md#92-video) |
| `track` | Timed text | [Chapter 9](../chapters/09-audio-video-and-embedded-content.md#92-video) |
| `iframe` | Embedded page | [Chapter 9](../chapters/09-audio-video-and-embedded-content.md#94-embedding-another-page) |
| `map`, `area` | Image-map regions | [Appendix 2, recognition](../appendices/02-less-common-html-and-platform-boundaries.md#a22-image-maps) |
| `canvas` | Scriptable bitmap drawing surface | [Appendix 2, recognition](../appendices/02-less-common-html-and-platform-boundaries.md#a23-canvas) |

## Tables

| Element | Purpose | Learn |
| --- | --- | --- |
| `table` | Tabular data | [Chapter 11](../chapters/11-tables-and-structured-data.md) |
| `caption` | Table title | [Chapter 11](../chapters/11-tables-and-structured-data.md#112-a-basic-accessible-table) |
| `thead`, `tbody`, `tfoot` | Row groups | [Chapter 11](../chapters/11-tables-and-structured-data.md) |
| `tr` | Table row | [Chapter 11](../chapters/11-tables-and-structured-data.md) |
| `th` | Header cell | [Chapter 11](../chapters/11-tables-and-structured-data.md) |
| `td` | Data cell | [Chapter 11](../chapters/11-tables-and-structured-data.md) |
| `colgroup`, `col` | Column grouping | [Chapter 11](../chapters/11-tables-and-structured-data.md#117-column-groups) |

## Forms

| Element | Purpose | Learn |
| --- | --- | --- |
| `form` | Submission interface | [Chapters 12–13](../chapters/12-forms-and-input-controls.md) |
| `label` | Control label | [Chapter 12](../chapters/12-forms-and-input-controls.md#122-labels-are-essential) |
| `input` | Single-value or file control | [Chapter 12](../chapters/12-forms-and-input-controls.md#123-input-types) |
| `textarea` | Multiline text control | [Chapter 12](../chapters/12-forms-and-input-controls.md#124-multiline-input) |
| `select` | Option-selection control | [Chapter 12](../chapters/12-forms-and-input-controls.md#125-select-menus) |
| `option` | Selectable option or suggestion | [Chapter 12](../chapters/12-forms-and-input-controls.md#125-select-menus) |
| `optgroup` | Labeled option group | [Chapter 12](../chapters/12-forms-and-input-controls.md#125-select-menus) |
| `datalist` | Suggestions for an input | [Chapter 12](../chapters/12-forms-and-input-controls.md#suggestions-with-datalist) |
| `button` | Action control | [Chapter 12](../chapters/12-forms-and-input-controls.md#128-buttons) |
| `fieldset` | Related control group | [Chapter 12](../chapters/12-forms-and-input-controls.md#126-radio-buttons) |
| `legend` | Fieldset group label | [Chapter 12](../chapters/12-forms-and-input-controls.md#126-radio-buttons) |
| `output` | Calculation or action result | [Chapter 16](../chapters/16-native-interactive-html.md#167-output) |

## Native interaction and component recognition

| Element | Purpose | Learn |
| --- | --- | --- |
| `details`, `summary` | Disclosure and its control | [Chapter 16](../chapters/16-native-interactive-html.md#162-disclosure-with-details-and-summary) |
| `dialog` | Dialog interface | [Chapter 16](../chapters/16-native-interactive-html.md#163-dialogs) |
| `progress` | Task completion | [Chapter 16](../chapters/16-native-interactive-html.md#165-progress) |
| `meter` | Scalar value in a known range | [Chapter 16](../chapters/16-native-interactive-html.md#166-meter) |
| `template` | Inert fragment for later use | [Appendix 2, recognition](../appendices/02-less-common-html-and-platform-boundaries.md#a24-templates) |
| `slot` | Web Component insertion point | [Appendix 2, recognition](../appendices/02-less-common-html-and-platform-boundaries.md#a25-custom-elements-and-slots) |

## Common global attributes

| Attribute | Purpose | Learn |
| --- | --- | --- |
| `id` | Unique document identifier | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#172-id-and-class) |
| `class` | Reusable classifications | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#172-id-and-class) |
| `lang` | Human language | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#174-language-changes) |
| `dir` | Text direction | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#175-directionality) |
| `translate` | Translation eligibility hint | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#176-translation-and-editing-hints) |
| `hidden` | Content not currently relevant | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#177-hidden-content) |
| `hidden="until-found"` | Hidden content revealable through find/fragment support | [Chapter 17, advanced](../chapters/17-advanced-attributes-and-language-features.md#177-hidden-content) |
| `inert` | Prevent focus and interaction within a subtree | [Chapter 17, advanced](../chapters/17-advanced-attributes-and-language-features.md#177-hidden-content) |
| `data-*` | Custom application data | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#173-custom-data-attributes) |
| `tabindex` | Focus participation | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#178-tabindex) |
| `accesskey` | Browser-mediated keyboard shortcut | [Chapter 17, recognition/caution](../chapters/17-advanced-attributes-and-language-features.md#accesskey-caution) |
| `contenteditable` | User editing behavior | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#176-translation-and-editing-hints) |
| `spellcheck` | Spelling/grammar checking hint | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#176-translation-and-editing-hints) |
| `title` | Advisory information | [Chapter 17](../chapters/17-advanced-attributes-and-language-features.md#171-global-attributes) |

## Form attributes worth distinguishing

| Attribute | Purpose | Learn |
| --- | --- | --- |
| `type` | Control type and behavior | [Chapter 12](../chapters/12-forms-and-input-controls.md#type-autocomplete-and-input-mode) |
| `autocomplete` | Meaning of autofill data | [Chapter 12](../chapters/12-forms-and-input-controls.md#type-autocomplete-and-input-mode) |
| `inputmode` | Suggested input modality | [Chapter 12](../chapters/12-forms-and-input-controls.md#type-autocomplete-and-input-mode) |
| `enterkeyhint` | Suggested virtual Enter-key action label | [Chapter 12, advanced](../chapters/12-forms-and-input-controls.md#type-autocomplete-and-input-mode) |
| `autocapitalize` | Suggested virtual-keyboard capitalization | [Chapter 12, advanced](../chapters/12-forms-and-input-controls.md#type-autocomplete-and-input-mode) |
| `capture` | Suggested direct media capture for a file input | [Chapter 12, advanced](../chapters/12-forms-and-input-controls.md#type-autocomplete-and-input-mode) |
| `form` | Explicit form owner by form ID | [Chapter 12, advanced](../chapters/12-forms-and-input-controls.md#controls-associated-from-elsewhere) |
| `name` | Submitted field name | [Chapter 12](../chapters/12-forms-and-input-controls.md#122-labels-are-essential) |
| `value` | Current or submitted value | [Chapter 12](../chapters/12-forms-and-input-controls.md) |
| `required`, `min`, `max`, `pattern` | Constraint validation | [Chapter 13](../chapters/13-validation-and-form-submission.md) |
| `multiple` | Permit multiple selected values/files | [Chapter 12](../chapters/12-forms-and-input-controls.md#multiple-values) |

## Link and metadata attributes worth distinguishing

| Attribute | Purpose | Learn |
| --- | --- | --- |
| `href` | Destination URL or related-resource address | [Chapters 6 and 14](../chapters/06-links-paths-and-navigation.md) |
| `rel` | Relationship between the current and linked resources | [Chapters 6 and 14](../chapters/14-document-head-and-metadata.md) |
| `hreflang` | Human language of a linked resource | [Chapter 14](../chapters/14-document-head-and-metadata.md#alternate-language-documents) |
| `media` | Intended media condition for a linked resource | [Chapter 14](../chapters/14-document-head-and-metadata.md) |
