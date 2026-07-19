# Appendix 1: Performance, Security, and Privacy

[Course home](../HTML_CRASH_COURSE.md) | Previous: [Chapter 20](../chapters/20-capstone-and-next-steps.md) | [Next appendix](02-less-common-html-and-platform-boundaries.md)

## Status of this appendix

This appendix is optional. It explains decisions that become important when a page leaves a private exercise folder and serves real users. It does not replace specialist performance testing, application security, legal advice, or server configuration.

## Learning objectives

After this appendix, you should be able to:

- Explain how HTML choices affect loading cost.
- Use lazy loading and priority hints cautiously.
- Identify privacy and security costs of third-party resources.
- Apply least privilege to embedded content.
- Distinguish HTML controls from server-enforced security policies.
- Minimize personal information collected by forms.

## A1.1 Performance is part of usability

A page may contain correct semantics and still be difficult to use if it downloads excessive media or delays important content. Slow pages particularly affect people using mobile data, older devices, unstable connections, or assistive technology that must wait for the document.

Begin with the highest-value questions:

1. Is this resource necessary?
2. Is its format and size appropriate?
3. Is it needed immediately?
4. Does the browser already have enough information to reserve its space?
5. Are we loading the same information twice?

Removing an unnecessary resource is more effective than adding a hint about how to fetch it.

## A1.2 Image loading

Images below the first visible screen may be candidates for lazy loading:

```html
<img
  src="images/workshop-room.jpg"
  alt="Students collaborating in the workshop room"
  width="1200"
  height="800"
  loading="lazy"
  decoding="async">
```

`loading="lazy"` tells the browser that it may defer fetching an off-screen image. It is a hint implemented by the browser, not a promise about an exact distance or time.

`decoding="async"` indicates that image decoding may happen without blocking other presentation work. The browser still makes the final scheduling decision.

Do not lazily load the primary image likely to appear immediately at the top of the page. Delaying important above-the-fold content can make performance worse.

Always provide correct `width` and `height` when known. Reserving the image's aspect ratio reduces content movement while the file loads.

## A1.3 Fetch priority

The `fetchpriority` attribute hints that a resource is relatively more or less important than similar resources:

```html
<img
  src="images/event-hero.jpg"
  alt="Community members attending the annual science fair"
  width="1600"
  height="900"
  fetchpriority="high">
```

Possible values are `high`, `low`, and `auto`. Use this only when measurement identifies a priority problem. Marking many resources `high` makes the signal meaningless and can delay resources the browser would otherwise schedule well.

Priority is not loading order, and it does not make a large file small.

## A1.4 Lazy iframes

An off-screen iframe can request lazy loading:

```html
<iframe
  src="https://maps.example.org/community-center"
  title="Map showing the community center"
  width="800"
  height="450"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin">
</iframe>
```

The `referrerpolicy` controls how much referring-page information is sent during navigation. Policy choice depends on the resource and site requirements; do not copy a value without understanding the privacy and compatibility consequences.

Lazy loading reduces initial work but does not remove the iframe's eventual privacy, performance, or security cost.

## A1.5 Third-party resources

A third-party resource comes from an organization or origin outside your control. Examples include:

- Embedded videos and maps.
- Analytics.
- Advertising.
- Social widgets.
- Remote fonts.
- JavaScript libraries from public CDNs.

Third parties may receive the visitor's IP address, referring information, browser details, and cookies. Their content may change, become unavailable, or introduce inaccessible behavior.

Before embedding:

1. State the user benefit.
2. Identify information transmitted.
3. Determine whether a normal link is sufficient.
4. Check consent and privacy requirements.
5. Provide fallback content.
6. Test failure when the third party is blocked.

## A1.6 Iframe least privilege

`sandbox` restricts an iframe:

```html
<iframe
  src="interactive-example.html"
  title="Interactive sorting example"
  sandbox>
</iframe>
```

Tokens can restore selected powers, but broad combinations can weaken the protection. Grant only capabilities the embedded page demonstrably requires.

The `allow` attribute controls selected powerful features:

```html
<iframe
  src="video-conference.html"
  title="Workshop video conference"
  allow="camera; microphone; fullscreen">
</iframe>
```

Camera and microphone permission should not be granted to an ordinary article or map. Browser permission prompts and server policies still apply.

## A1.7 Links and referrer information

For a link where the destination should not receive referrer information:

```html
<a
  href="https://external.example/"
  rel="noreferrer">
  Visit the external resource
</a>
```

`noreferrer` also implies opener isolation in common browser behavior. Use it because of an explicit privacy requirement, not as a ritual on every link.

`noopener` prevents a newly opened page from controlling its opener relationship:

```html
<a
  href="https://external.example/"
  target="_blank"
  rel="noopener">
  Open external reference in a new tab
</a>
```

Modern browsers commonly protect `_blank` links implicitly, but writing the relationship can document intent and support older contexts.

## A1.8 Subresource Integrity

Subresource Integrity, or SRI, lets a browser compare a fetched script or stylesheet with an expected cryptographic hash:

```html
<script
  src="https://cdn.example.org/library.js"
  integrity="sha384-REPLACE_WITH_REAL_HASH"
  crossorigin="anonymous">
</script>
```

The example hash is intentionally not functional. Never invent a hash. Obtain it from a trusted release process and update it when the resource changes.

SRI protects against unexpected resource contents; it does not prove that the intended library is safe, private, or suitable.

## A1.9 Content Security Policy

Content Security Policy, or CSP, restricts where a document may load scripts, styles, images, frames, and other resources. It is normally delivered as an HTTP response header by the server.

A limited policy can also be declared with `meta http-equiv`, but not every CSP feature works there, and the policy affects only content that follows the declaration. Treat CSP as a deployment and security-engineering concern rather than a copy-and-paste HTML feature.

Never weaken a policy simply to silence an error. Identify why the resource is needed and grant the narrowest justified source.

## A1.10 Form privacy and data minimization

Every requested field creates work and potential risk. Ask only for data necessary to complete the stated task.

For a free workshop, a birth date may be excessive if the only real requirement is confirmation that a participant meets a minimum age. A full postal address may be unnecessary for an online event.

For each field document:

- Purpose.
- Whether it is required.
- Who can access it.
- How long it is retained.
- How users can correct or remove it.

HTML can communicate labels, purpose, and constraints. It cannot enforce retention policies, access control, encryption at rest, or deletion. Those require organizational and server-side systems.

## A1.11 Security boundaries

HTML alone cannot provide:

- Authentication.
- Authorization.
- Secure password storage.
- Database validation.
- Malware scanning.
- Rate limiting.
- Audit logging.
- Safe email delivery.
- Legal compliance.

Client-side restrictions can be bypassed. Server validation and security controls remain authoritative.

## Performance, security, and privacy audit

For one project, record:

| Resource or field | User benefit | Cost or risk | Current control | Improvement |
| --- | --- | --- | --- | --- |
| Workshop image | Shows venue | 1.8 MB download | Dimensions set | Resize and compress |
| External map | Gives directions | Third-party request | Iframe title | Offer address and link |
| Birth date | Age check | Excess personal data | Required field | Ask age eligibility instead |

Then test:

- Page with images blocked.
- Page with third-party content blocked.
- Keyboard operation of every remaining feature.
- Network requests before and after removing optional resources.
- Whether every collected field has a documented purpose.

## Common misconceptions

- Lazy loading does not reduce a resource's file size.
- Priority hints do not override every browser decision.
- HTTPS does not make third-party collection private.
- `sandbox` and `allow` solve different permission problems.
- SRI does not certify library quality.
- CSP is primarily a deployment policy, not a beginner meta-tag trick.
- A required form field is not automatically a necessary field.

## Authoritative references

- [WHATWG: Images](https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element)
- [WHATWG: Lazy loading](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#lazy-loading-attributes)
- [WHATWG: Fetch priority](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#fetch-priority-attributes)
- [WHATWG: The iframe element](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-iframe-element)
- [W3C: Subresource Integrity](https://www.w3.org/TR/SRI/)
- [W3C: Content Security Policy](https://www.w3.org/TR/CSP3/)

[Next appendix: Less-common HTML and platform boundaries](02-less-common-html-and-platform-boundaries.md)
