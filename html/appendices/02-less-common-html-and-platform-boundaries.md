# Appendix 2: Less-common HTML and Platform Boundaries

[Course home](../HTML_CRASH_COURSE.md) | [Previous appendix](01-performance-security-and-privacy.md) | [Next appendix](03-browser-and-assistive-technology-lab.md)

## Status of this appendix

This is a recognition guide. You should understand what these features are when you encounter them, but you do not need them to complete the core course. Several become useful only with JavaScript, CSS, server configuration, or specialist accessibility testing.

## Learning objectives

After this appendix, you should be able to:

- Recognize less-common conforming elements.
- Explain why `base` can unexpectedly change every relative URL.
- Identify accessibility requirements for image maps and canvas.
- Explain the inert purpose of `template`.
- Recognize slots, custom elements, manifests, and structured data.
- State which technology layer must supply missing behavior.

## A2.1 The `base` element

`base` establishes a base URL or default target for relative URLs:

```html
<head>
  <base href="https://example.org/courses/html/">
  <title>Lesson</title>
</head>
```

After this declaration:

```html
<a href="exercises/one.html">Exercise one</a>
```

resolves against the declared base rather than the document's own address.

This is powerful and risky:

- It changes links, images, forms, scripts, stylesheets, and fragments that use relative URLs.
- It can make locally previewed paths behave unexpectedly.
- It must appear before URL-valued metadata that should use it.
- Only one document-wide base URL can apply.

Most beginner and small static sites should avoid `base` and use explicit relative paths. Learn it so you can diagnose inherited projects.

## A2.2 Image maps

An image map creates link regions over one image:

```html
<img
  src="images/campus-map.png"
  alt="Campus map"
  usemap="#campus-links"
  width="1000"
  height="700">

<map name="campus-links">
  <area
    shape="rect"
    coords="80,120,260,300"
    href="library.html"
    alt="Library">
  <area
    shape="circle"
    coords="650,250,80"
    href="laboratory.html"
    alt="Science laboratory">
</map>
```

Each linked `area` needs an alternative naming its destination. Coordinates can become inaccurate when images scale, and the visual regions may be difficult for keyboard, touch, zoom, or screen-magnification users.

Prefer an ordinary list of links alongside the image. For directions, include a textual address and instructions. Use an image map only when the spatial relationship genuinely matters and testing confirms usability.

## A2.3 Canvas

`canvas` provides a bitmap drawing surface:

```html
<canvas width="600" height="400">
  A chart showing monthly attendance. A data table follows.
</canvas>
```

JavaScript normally draws into the canvas. The pixels do not automatically create semantic headings, text, links, or controls. Provide an equivalent accessible representation, such as a data table for a chart or native controls for an interactive tool.

Canvas is appropriate for some games, drawing tools, and data visualizations. It is not a replacement for semantic page content. SVG may be more suitable when individual graphic objects need structure and scalability.

## A2.4 Templates

`template` holds markup that is not rendered when the document first loads:

```html
<template id="course-card-template">
  <article class="course-card">
    <h2>Course title</h2>
    <p>Course description</p>
  </article>
</template>
```

Its contents are inert until JavaScript clones or adopts them. IDs, forms, media, and scripts inside do not behave as ordinary live document content while they remain in the template.

HTML declares the reusable fragment. JavaScript decides when to create a live instance and how to populate it.

## A2.5 Custom elements and slots

A custom-element name contains a hyphen:

```html
<course-card>
  <span slot="title">Semantic HTML</span>
  <p>Learn to structure documents.</p>
</course-card>
```

JavaScript defines what `course-card` does. Without that definition, the unknown element remains an element but has no custom behavior or built-in semantics.

A `slot` is a placeholder used inside a component's shadow tree:

```html
<slot name="title">Untitled course</slot>
```

The fallback text appears when no matching slotted content is supplied. Slots do not create an ordinary page-layout system and are not useful outside the Web Components model.

When custom elements represent controls, their author must implement keyboard behavior, accessible names, states, focus, and form behavior. Native elements remain the first choice.

## A2.6 Declarative shadow DOM

You may encounter:

```html
<template shadowrootmode="open">
  <style>
    .component { display: block; }
  </style>
  <slot></slot>
</template>
```

This can declare a shadow root in HTML. Shadow DOM changes styling and DOM boundaries and requires knowledge beyond this course. Treat it as an advanced component feature, verify current browser support, and test accessibility across the boundary.

## A2.7 `noscript`

`noscript` provides content when scripting is disabled or unsupported:

```html
<noscript>
  <p>
    The interactive seat selector requires JavaScript.
    Call the registration desk to choose a seat.
  </p>
</noscript>
```

Use it for a truthful alternative or explanation. It is not a universal fallback for:

- A script that downloaded but failed.
- An unsupported JavaScript feature.
- A blocked network request.
- An application runtime error.

Where possible, start with functional HTML and enhance it with JavaScript. That strategy handles more failure modes than `noscript` alone.

## A2.8 Web app manifests

A manifest describes installable web-application metadata:

```html
<link rel="manifest" href="site.webmanifest">
```

The referenced JSON can describe names, icons, display mode, theme colors, and start URLs. A manifest does not by itself make a site installable, offline-capable, or a Progressive Web App. HTTPS, suitable icons, application behavior, and browser criteria also matter.

Manifest work belongs to later application and deployment study.

## A2.9 Structured data

Structured data gives software explicit information about entities such as events, products, people, or organizations.

HTML includes **microdata** attributes:

```html
<article itemscope itemtype="https://schema.org/Event">
  <h2 itemprop="name">Community Science Fair</h2>
  <time itemprop="startDate" datetime="2026-09-12">
    September 12, 2026
  </time>
</article>
```

Another common ecosystem approach is JSON-LD:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "Community Science Fair",
  "startDate": "2026-09-12"
}
</script>
```

Structured data must agree with visible content. It does not guarantee search-result features and must not invent reviews, dates, prices, or identities. Verify current vocabulary and search-platform requirements before publishing.

## A2.10 Recognition table

| Feature | HTML supplies | Another layer supplies |
| --- | --- | --- |
| `base` | URL-resolution base | Deployment-safe URL design |
| Image map | Spatial link regions | Responsive/accessibility testing |
| `canvas` | Drawing surface | JavaScript drawing and equivalent content |
| `template` | Inert fragment | JavaScript instantiation |
| Custom element | Valid named element | JavaScript definition and behavior |
| `slot` | Component insertion point | Shadow DOM component design |
| `noscript` | No-script branch | General failure recovery |
| Manifest | App metadata link | Installability and offline behavior |
| Structured data | Machine-readable facts | Accurate domain vocabulary and validation |

## Recognition exercise

For each requirement, choose native core HTML, one feature from this appendix, or a later technology:

1. Show a readable list of campus buildings.
2. Draw a real-time multiplayer game.
3. Reuse an inert card fragment from JavaScript.
4. Define an installable application's icons.
5. Make a normal contact form save to a database.
6. Mark an event's visible name and date for structured-data consumers.

Defend the simplest solution. An advanced feature is not automatically the best feature.

## Common misconceptions

- `base` does not affect only anchors; it changes relative URL resolution broadly.
- Image maps do not replace textual navigation.
- Canvas pixels are not a semantic document tree.
- Template content is not live page content.
- A custom element name does not create behavior.
- `noscript` does not catch every JavaScript failure.
- A manifest does not create offline capability.
- Structured data must match visible, truthful content.

## Authoritative references

- [WHATWG: The base element](https://html.spec.whatwg.org/multipage/semantics.html#the-base-element)
- [WHATWG: Image maps](https://html.spec.whatwg.org/multipage/image-maps.html)
- [WHATWG: The canvas element](https://html.spec.whatwg.org/multipage/canvas.html#the-canvas-element)
- [WHATWG: The template element](https://html.spec.whatwg.org/multipage/scripting.html#the-template-element)
- [WHATWG: The slot element](https://html.spec.whatwg.org/multipage/scripting.html#the-slot-element)
- [WHATWG: Microdata](https://html.spec.whatwg.org/multipage/microdata.html)

[Next appendix: Browser and assistive-technology lab](03-browser-and-assistive-technology-lab.md)
