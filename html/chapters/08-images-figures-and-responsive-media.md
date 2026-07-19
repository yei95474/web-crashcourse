# Chapter 8: Images, Figures, and Responsive Media

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Lists and Content Grouping](07-lists-and-content-grouping.md) | [Next: Audio, Video, and Embedded Content](09-audio-video-and-embedded-content.md)

## Prerequisites

- Chapters 1-7
- Comfort with relative paths

## Learning objectives

You will learn to:

- Embed images with useful source paths and intrinsic dimensions.
- Write alternative text according to an image's purpose.
- Pair self-contained media with captions.
- Distinguish content images from decorative images.
- Understand raster and vector formats.
- Use `srcset`, `sizes`, and `picture` for responsive image decisions.
- Choose loading, decoding, and priority hints according to evidence.

## Suggested study time

- Reading and media analysis: 55-70 minutes
- Practice, lab, and project work: 50-75 minutes

## Key vocabulary

- **Alternative text**: a textual replacement that communicates an image's purpose.
- **Intrinsic dimensions**: the width and height associated with an image resource.
- **Raster image**: an image represented by a grid of pixels.
- **Vector image**: an image represented by shapes and drawing instructions.
- **Responsive image**: markup that helps select an appropriate image for the context.
- **Resolution switching**: choosing among equivalent images with different resolutions.
- **Art direction**: supplying meaningfully different crops or compositions for different conditions.
- **Lazy loading**: delaying an off-screen resource until it approaches the viewport.

## 8.1 Images are resources, not page decorations by default

The `img` element embeds an image resource:

```html
<img
  src="images/campus-library.jpg"
  alt="Students studying at tables inside the campus library"
  width="1200"
  height="800">
```

- `src` gives the resource path.
- `alt` supplies a text alternative.
- `width` and `height` provide intrinsic dimensions in CSS pixels and let the browser reserve the correct aspect-ratio space while loading.

`img` is void: it has no closing tag or child content.

Store project images in a predictable folder. Use meaningful lowercase names such as `campus-library.jpg`, not `IMG_0042_FINAL2.jpg`.

## 8.2 Alternative text is a design decision

Alternative text replaces the image when the image cannot be perceived or loaded. Write it according to the image's **purpose in context**, not by mechanically listing everything visible.

### Informative image

```html
<img
  src="images/fire-exit-map.png"
  alt="Fire exit route from Room 204: turn left, then use the north stairs">
```

The route is the important information.

### Functional image

If an image is the only content of a link or button, its alt text names the action or destination:

```html
<a href="index.html">
  <img src="images/home-icon.svg" alt="Home">
</a>
```

Do not write `alt="home icon"` if the user's action is going home.

### Decorative image

If an image contributes no information and adjacent content already communicates everything:

```html
<img src="images/flourish.svg" alt="">
```

The empty attribute tells assistive technology to ignore it. Omitting `alt` can cause a screen reader to announce the filename.

### Complex image

Charts, diagrams, and maps may need a short `alt` plus a nearby detailed explanation or data table. Do not force an entire report into one attribute.

Avoid phrases such as “image of” unless the fact that something is an image matters. Screen readers usually announce the image role already.

## 8.3 Figures and captions

Use `figure` for self-contained content referenced as a unit, and `figcaption` for its caption:

```html
<figure>
  <img
    src="images/growth-chart.png"
    alt="Enrollment rose from 400 students in 2022 to 650 in 2026">
  <figcaption>Figure 1. Enrollment by year.</figcaption>
</figure>
```

The caption is visible to everyone. It can identify, number, credit, or explain the figure. Avoid needless duplication between `alt` and `figcaption`.

`figure` can also contain code, quotations, tables, or illustrations, not only images.

## 8.4 Formats

Common raster formats:

- **JPEG**: photographs; no transparency; lossy compression.
- **PNG**: sharp graphics and transparency; often larger for photographs.
- **WebP** and **AVIF**: modern compression for photos or graphics.
- **GIF**: simple animation, limited color; video is often more efficient for substantial motion.

**SVG** is vector graphics described with markup. It scales without pixelation and works well for icons, logos, and diagrams. SVG can be loaded through `img`; inline SVG is more advanced and should come from a trusted source.

Choose a format based on content, quality, file size, transparency, animation, and browser support. Huge images slow users and consume mobile data even if displayed small.

## 8.5 Responsive resolution with `srcset`

Provide alternate resolutions of the same image:

```html
<img
  src="images/coast-800.jpg"
  srcset="
    images/coast-480.jpg 480w,
    images/coast-800.jpg 800w,
    images/coast-1600.jpg 1600w
  "
  sizes="(max-width: 600px) 100vw, 800px"
  alt="Rocky coastline under a cloudy sky"
  width="1600"
  height="900">
```

Each `w` descriptor gives an image's intrinsic width. `sizes` describes the expected rendered width under layout conditions. The browser chooses a suitable candidate based on viewport, pixel density, network policy, and other factors.

The browser makes the choice; do not assume it always selects the smallest file.

## 8.6 Art direction with `picture`

Use `picture` when different conditions require different crops or formats:

```html
<picture>
  <source
    media="(max-width: 600px)"
    srcset="images/team-close.jpg">
  <img
    src="images/team-wide.jpg"
    alt="The robotics team presenting its competition robot"
    width="1200"
    height="675">
</picture>
```

The `img` is required as the default and carries the accessible alternative. `source` elements offer candidates; they do not replace `img`.

Responsive images are advanced. First master correct paths and alt decisions, then add optimization only when you have real alternate assets.

## 8.7 Loading and priority decisions

For an image below the initially visible area:

```html
<img
  src="images/workshop-room.jpg"
  alt="Students collaborating in the workshop room"
  width="1200"
  height="800"
  loading="lazy"
  decoding="async">
```

`loading="lazy"` tells the browser it may defer an off-screen image. `decoding="async"` indicates that decoding may occur without blocking other presentation work. Both are hints; the browser controls the final schedule.

Do not lazily load a primary image expected to be visible immediately. Delaying it can make the page feel slower.

`fetchpriority` gives a relative priority hint:

```html
<img
  src="images/event-hero.jpg"
  alt="Visitors entering the community science fair"
  width="1600"
  height="900"
  fetchpriority="high">
```

Use priority hints only when measurement identifies a problem. Marking every resource high defeats the purpose. Correct file size, format, dimensions, and necessity matter more than hints.

## 8.8 Practice

**C08-Q1 - Fill in the blanks.**

```html
<img ____="images/robot.jpg" ____="Student-built robot lifting a cube">
```

**C08-Q2 - Accessibility decision.** A decorative divider repeats no information. Should its alt text be omitted, empty, or a visual description?

**C08-Q3 - Functional image.** An image is the only content in a link to the shopping cart. Which is better: `alt="cart icon"` or `alt="Shopping cart"`? Why?

**C08-Q4 - Spot the bug.** Identify two problems:

```html
<img src="C:\photos\Dog.JPG">
```

**C08-Q5 - Semantic choice.** Which element provides a visible caption associated with a `figure`?

**C08-Q6 - Pause and predict.** In a `picture`, which element supplies the fallback and alternative text?

**C08-Q7 - Core challenge.** Write an image with a relative path, meaningful alt text, and dimensions of 800 by 600.

**C08-Q8 - Performance choice.** A large photograph appears near the end of a long article. Which loading attribute may defer it, and why should the same choice not be applied automatically to the page's main hero image?

## Guided lab: improve the recipe site

Add one food photograph to the Chapter 7 recipe:

1. Place it in `images/`.
2. Rename it descriptively.
3. Add it inside `figure`.
4. Write purpose-based alt text.
5. Add a visible source or explanatory caption.
6. Set correct intrinsic dimensions.
7. Temporarily misspell the path to observe fallback behavior, then restore it.

## Project 2: recipe or hobby site

Expand the site to at least two linked pages containing headings, paragraphs, lists, navigation, and two appropriately described images. One image must use `figure`; one may be decorative only if its empty alt is justified in a source comment.

Use the [small-site rubric](../reference/project-rubrics.md#project-2-recipe-or-hobby-site).

## Stretch challenge: alt-text laboratory

Imagine one photograph of a flooded street used in three articles:

1. A news report about the flood's depth.
2. A profile of the photographer.
3. A page where the photo is decorative beside an already complete headline.

Write a different alt decision for each context. Explain why identical pixels can require different text alternatives.

## Common misconceptions

- `alt` is not a filename, tooltip, or photo caption.
- Decorative images need `alt=""`, not a missing attribute.
- Width and height attributes are not permission to download an oversized image.
- `figure` is not required for every image.
- `picture` offers image choices; its `img` remains essential.

## Chapter summary

Images are external resources with paths, alternatives, and intrinsic dimensions. Good alt text communicates purpose in context. Figures connect self-contained media to visible captions. Responsive image features let browsers choose suitable resources, while formats balance visual quality and transfer cost.

## Mastery checklist

- [ ] I can embed an image with a portable path.
- [ ] I can classify an image as informative, functional, decorative, or complex.
- [ ] I always make an intentional `alt` decision.
- [ ] I can use `figure` and `figcaption`.
- [ ] I understand raster versus vector graphics.
- [ ] I can explain the roles of `srcset`, `sizes`, `picture`, `source`, and `img`.
- [ ] I understand that loading, decoding, and priority attributes are browser hints.

Solutions: [Media, structure, and tables answer key](../answer-keys/03-media-structure-and-tables.md#chapter-8)

## Authoritative references

- [WHATWG: The img element](https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element)
- [WHATWG: Lazy loading](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#lazy-loading-attributes)
- [W3C WAI: Images tutorial](https://www.w3.org/WAI/tutorials/images/)

[Next: Chapter 9 - Audio, Video, and Embedded Content](09-audio-video-and-embedded-content.md)
