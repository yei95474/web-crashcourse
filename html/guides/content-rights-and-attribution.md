# Content Rights and Attribution Guide

[Course home](../HTML_CRASH_COURSE.md) | [Project workflow](project-workflow.md) | [Project rubrics](../reference/project-rubrics.md)

## Why this belongs in an HTML course

A webpage can be technically valid and still misuse someone else's writing, photograph, illustration, audio, video, logo, font, or data. Professional authors identify the source, permission, license, privacy risk, and accessibility requirements of content before publishing it.

This chapter provides general educational practice, not jurisdiction-specific legal advice. Copyright exceptions and privacy requirements vary. Ask an instructor, organization, or qualified professional when a real publication carries legal or contractual risk.

## A source is not permission

Finding material through a search engine tells you where a copy was discovered. It does not prove that you may republish, edit, sell, or redistribute it.

Before using material, identify one defensible basis:

- You created it and retained the relevant rights.
- The rights holder gave suitable permission.
- A license permits the intended use and you follow its conditions.
- The work is genuinely in the public domain in the relevant context.
- A specific legal exception applies and responsible institutional guidance supports that conclusion.

“It is educational,” “I gave credit,” and “it was publicly visible” are not universal permissions.

## Read the actual license

Creative Commons licenses are standardized permissions with different conditions. Common condition abbreviations include:

- **BY**: give attribution.
- **SA**: license adaptations under the same terms.
- **NC**: restrict use to noncommercial purposes under the license's definition.
- **ND**: do not distribute adaptations.
- **CC0**: a public-domain dedication tool with no license conditions, though accurate source notes remain good scholarly practice.

Do not assume every “free” or Creative Commons work permits every use. Confirm the exact license version and whether cropping, translating, editing, combining, or commercial publication is allowed.

Official overview: [Creative Commons licenses](https://creativecommons.org/share-your-work/use-remix/cc-licenses/).

## A practical attribution record

For each external asset, record:

| Field | Example |
| --- | --- |
| Title or description | “Students building a weather station” |
| Creator | Ana Example |
| Source URL | Direct page where the work and license are identified |
| License or permission | CC BY 4.0 |
| License URL | `https://creativecommons.org/licenses/by/4.0/` |
| Changes | Cropped and reduced to 1200 × 800 |
| Retrieved | 2026-07-14 |

One concise page attribution might be:

```html
<p>
  “Students building a weather station” by Ana Example,
  licensed under
  <a href="https://creativecommons.org/licenses/by/4.0/">
    CC BY 4.0
  </a>. Cropped from the original.
</p>
```

Link the creator and original source when appropriate. Place attribution where readers can find it and where its relationship to the work is clear. Do not imply that the creator endorses your project.

## Your own licensing notice

Do not apply a license to material you do not control. A site-wide notice should identify exceptions:

```html
<p>
  Except where otherwise noted, original text is licensed under
  <a href="https://creativecommons.org/licenses/by/4.0/">
    CC BY 4.0
  </a>. Third-party images retain their stated licenses.
</p>
```

Before licensing a team project, confirm that contributors agreed and that employment, school, sponsor, or client rules do not assign rights elsewhere.

## Privacy, consent, and student safety

Permission to take or possess a photograph is not automatically permission to publish it globally. Before publishing identifiable people or personal information, consider:

- Informed consent and the person's ability to withdraw it.
- Children and other people requiring additional protection.
- Names, uniforms, badges, addresses, schedules, geolocation, and background details.
- Whether the learning goal can be met with fictional, anonymized, or non-identifying content.
- How long the content will remain available and who can copy it.

Course projects should use fictional organizations and synthetic data unless real publication is deliberately authorized. Never require students to reveal personal histories, contact details, disability information, or precise locations to prove HTML skill.

## Accessibility still applies to licensed material

A license does not make an asset accessible. You still need to:

- Write purpose-based alternative text for images.
- Supply captions and transcripts for relevant media.
- Communicate important visual information in text or description.
- Avoid text embedded in images when ordinary HTML text can work.
- Check that external players and embeds are keyboard-operable.

W3C guidance: [Making Audio and Video Media Accessible](https://www.w3.org/WAI/media/av/).

## Artificially generated and supplied content

For generated, commissioned, client-supplied, or AI-assisted material:

- Record the tool or source when course or organizational policy requires disclosure.
- Verify factual claims and inspect for copied logos, recognizable people, private data, or misleading representations.
- Confirm that the applicable service terms and project agreement permit the intended use.
- Do not present generated citations, permissions, or license claims as verified evidence.
- Keep a human accountable for accessibility, accuracy, and publication decisions.

## Project content ledger

Maintain this table while building:

| Asset | Owner/source | Permission or license | Changes | Attribution location | Accessibility work | Approved? |
| --- | --- | --- | --- | --- | --- | --- |
| `images/team.jpg` |  |  |  |  |  |  |
| Interview audio |  |  |  |  |  |  |
| Event statistics |  |  |  |  |  |  |

An unknown license or missing consent is a blocker for publication, not a note to fix after launch. Replace uncertain assets with your own work, clearly licensed material, or a text placeholder.

## Pre-publication checklist

- [ ] Every non-original asset has a recorded source.
- [ ] The intended use follows the actual permission or license.
- [ ] Required attribution and modification notices are present.
- [ ] Site-wide licensing does not claim third-party work.
- [ ] Identifiable people and personal information have appropriate authorization.
- [ ] Student projects avoid unnecessary real personal data.
- [ ] Images and media have suitable accessibility alternatives.
- [ ] Generated or supplied content has been reviewed by a responsible human.
- [ ] Uncertain content has been removed or replaced before publication.

## Further references

- [Creative Commons: About CC Licenses](https://creativecommons.org/share-your-work/cclicenses/)
- [Creative Commons: License Your Work](https://creativecommons.org/cc-license-your-work/)
- [W3C WAI: Making Audio and Video Media Accessible](https://www.w3.org/WAI/media/av/)

[Project workflow](project-workflow.md)
