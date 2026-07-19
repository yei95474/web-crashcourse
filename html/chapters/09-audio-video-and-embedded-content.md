# Chapter 9: Audio, Video, and Embedded Content

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Images, Figures, and Responsive Media](08-images-figures-and-responsive-media.md) | [Next: Semantic Page Structure](10-semantic-page-structure.md)

## Prerequisites

- Chapters 1-8
- Relative paths and image alternatives

## Learning objectives

You will learn to:

- Embed audio and video with browser controls and fallback content.
- Offer multiple media formats.
- Associate captions and subtitles with video.
- Avoid inaccessible autoplay behavior.
- Embed external pages with descriptive titles and appropriate permissions.
- Recognize performance, privacy, and security costs.
- Apply iframe loading and referrer controls deliberately.

## Suggested study time

- Reading and examples: 45-60 minutes
- Practice and guided lab: 40-55 minutes

## Key vocabulary

- **Media player**: an interface that presents audio or video and playback controls.
- **Caption**: synchronized text representing speech and important sounds.
- **Subtitle**: synchronized translation or transcription, often assuming sound can be heard.
- **Transcript**: a separate text version of audio or audiovisual content.
- **Fallback content**: an alternative presented when the preferred resource cannot be used.
- **Iframe**: an element that embeds another browsing context or webpage.
- **Sandbox**: restrictions applied to embedded content to reduce its capabilities.
- **Third party**: an external organization or service supplying a resource or embed.

## 9.1 Native media players

HTML supplies built-in media elements. A basic audio player:

```html
<audio controls>
  <source src="media/interview.mp3" type="audio/mpeg">
  <source src="media/interview.ogg" type="audio/ogg">
  <p>
    Your browser cannot play this audio.
    <a href="media/interview.mp3">Download the interview</a>.
  </p>
</audio>
```

The `controls` boolean attribute lets users play, pause, seek, and adjust volume. Multiple `source` elements let the browser select a supported format without downloading every option.

Fallback content appears when the element is unsupported. A direct link also helps users who prefer another player.

## 9.2 Video

```html
<video controls width="960" height="540" poster="images/lab-poster.jpg">
  <source src="media/lab-tour.webm" type="video/webm">
  <source src="media/lab-tour.mp4" type="video/mp4">
  <track
    kind="captions"
    src="media/lab-tour-en.vtt"
    srclang="en"
    label="English"
    default>
  <p>
    Your browser cannot play this video.
    <a href="media/lab-tour.mp4">Download the lab tour</a>.
  </p>
</video>
```

- `poster` is shown before playback.
- `track` associates timed text, commonly a WebVTT file.
- `kind="captions"` identifies dialogue plus meaningful sounds for people who cannot hear the audio.
- `srclang` identifies the track language.
- `default` suggests the initially enabled track.

Captions are not the same as subtitles. Subtitles generally translate or transcribe dialogue for viewers who can hear other audio; captions also communicate speakers and meaningful sounds. A transcript provides a separate text version and is valuable for audio-only content, search, review, and users who cannot operate the player conveniently.

Audio description communicates important visual information not available in dialogue.

## 9.3 Autoplay and user control

Avoid autoplay with sound. Unexpected audio can interfere with screen readers, startle users, consume data, and create social problems. Browsers often block it.

If ambient decorative video is genuinely needed later, it generally requires muted playback, a pause control, careful performance work, and a reduced-motion strategy. That is outside this HTML-first course.

Do not remove native controls until you have the JavaScript and accessibility knowledge to provide a fully equivalent interface.

## 9.4 Embedding another page

An `iframe` creates a nested browsing context:

```html
<iframe
  src="https://example.org/map"
  title="Map showing the community center"
  width="800"
  height="450"
  loading="lazy">
</iframe>
```

The `title` identifies the frame to assistive-technology users. It should describe the embedded content, not merely say “iframe.”

Only embed content whose provider permits embedding. External content may:

- Set cookies or track visitors.
- Load large scripts and media.
- Change or disappear without your control.
- Contain keyboard traps or inaccessible controls.
- Slow the page.

A plain link can be safer, faster, and more accessible.

## 9.5 Permissions and sandboxing

Modern iframes can restrict capabilities:

```html
<iframe
  src="embedded-demo.html"
  title="Interactive sorting demonstration"
  sandbox>
</iframe>
```

An empty `sandbox` applies many restrictions. Tokens can restore specific capabilities, but choosing them requires understanding the embedded application. Do not copy permissive combinations without evaluating the trust boundary.

The `allow` attribute grants selected features such as fullscreen or camera access. Grant only what the content needs.

This is a security principle called **least privilege**: begin with minimal capability and add only justified permissions.

## 9.6 `embed` and `object`

HTML also has `embed` and `object` for external resources. Their behavior and accessibility can be inconsistent for formats such as PDFs. Prefer a normal link when users need reliable access:

```html
<p>
  <a href="files/annual-report.pdf">
    Download the annual report (PDF, 2.4 MB)
  </a>
</p>
```

Including the format and size helps people decide before downloading.

## 9.7 Iframe loading, referrers, and third parties

An off-screen iframe may request lazy loading and a specific referrer policy:

```html
<iframe
  src="https://maps.example.org/community-center"
  title="Map showing the community center"
  width="800"
  height="450"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin"
  sandbox>
</iframe>
```

- `loading="lazy"` may defer the off-screen nested page.
- `referrerpolicy` controls how much referring-page information accompanies the request.
- `sandbox` begins with restrictions; tokens selectively restore capabilities.
- `allow` can grant selected features such as camera, microphone, or fullscreen.

Do not copy this exact combination as universal boilerplate. A heavily sandboxed third-party map may not function, while a permissive frame may expose unnecessary capability. Identify requirements, grant the least privilege, and test the failure state.

Loading an external iframe can disclose visitor information and create network requests even before the user interacts. When a normal address and link satisfy the need, they are often the simpler privacy-preserving choice.

## 9.8 Practice

**C09-Q1 - Warm-up.** Which boolean attribute exposes the browser's media controls?

**C09-Q2 - Semantic choice.** Which `track` kind communicates dialogue and meaningful sounds for viewers who cannot hear?

**C09-Q3 - Fill in the blank.**

```html
<iframe src="map.html" _____="Campus accessibility map"></iframe>
```

**C09-Q4 - Pause and predict.** Does a browser download and play every `source` inside one `video`, or select a suitable source?

**C09-Q5 - Accessibility reasoning.** Give two reasons to avoid autoplay with sound.

**C09-Q6 - Security reasoning.** State the least-privilege principle in your own words.

**C09-Q7 - Core challenge.** Write a basic audio element with controls, one MP3 source, and fallback download text.

**C09-Q8 - Privacy decision.** A page can show directions either through a third-party map iframe or a street address with an external map link. Name one privacy and one performance reason to prefer the link.

## Guided lab: accessible interview

Plan, but do not necessarily record, an interview page containing:

1. A meaningful heading and introduction.
2. An audio element with controls.
3. A direct download link.
4. A complete transcript below the player.
5. Speaker names marked clearly.
6. No autoplay.

If you have no media file, use placeholder paths and focus on structure.

## Stretch challenge: embed or link?

For each case, choose embed, native media, or plain link and justify:

1. A third-party map that sets tracking cookies.
2. A short video you own with captions.
3. A 20 MB PDF handbook.
4. An interactive calculator from an unknown site.

Consider purpose, control, privacy, performance, accessibility, and security.

## Common misconceptions

- Native controls are not an amateur feature; they provide tested interaction.
- Captions, subtitles, transcripts, and audio description solve different needs.
- An iframe is an entire nested page, not merely a visual rectangle.
- `title` on an iframe is not optional decoration.
- Embedding does not transfer ownership or reliability to you.
- More permission is not automatically more compatible.

## Chapter summary

Native audio and video elements provide browser controls, multiple source options, fallback links, and timed-text tracks. Accessible media requires captions or transcripts according to its content. Iframes embed independent pages and carry privacy, security, performance, and accessibility responsibilities.

## Mastery checklist

- [ ] I can create audio and video players with controls.
- [ ] I can explain source selection and fallback content.
- [ ] I distinguish captions, subtitles, transcripts, and audio description.
- [ ] I avoid unexpected autoplay.
- [ ] I give every iframe a useful title.
- [ ] I evaluate whether linking is better than embedding.
- [ ] I understand least privilege.
- [ ] I can explain iframe loading, referrer, sandbox, and permission decisions.

Solutions: [Media, structure, and tables answer key](../answer-keys/03-media-structure-and-tables.md#chapter-9)

## Authoritative references

- [WHATWG: Video and audio](https://html.spec.whatwg.org/multipage/media.html)
- [WHATWG: The iframe element](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-iframe-element)
- [W3C WAI: Audio and video media](https://www.w3.org/WAI/media/av/)

[Next: Chapter 10 - Semantic Page Structure](10-semantic-page-structure.md)
