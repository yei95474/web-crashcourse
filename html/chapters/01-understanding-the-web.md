# Chapter 1: Understanding the Web

[Course home](../HTML_CRASH_COURSE.md) | Previous: Course home | [Next: Files, Editors, and Workspaces](02-files-editors-and-workspaces.md)

## Prerequisites

No technical knowledge is required. You only need experience opening websites in a browser.

## Learning objectives

By the end of this chapter, you should be able to:

- Distinguish the Internet, the Web, a website, and a webpage.
- Describe the client-server request-and-response cycle.
- Identify the important parts of a URL.
- Explain status codes, media types, and web origins at a beginner level.
- Explain the different responsibilities of HTML, CSS, and JavaScript.
- Distinguish a local page from a published page.
- Distinguish a specification, browser implementation, tutorial, and compatibility result.

## Suggested study time

- Reading and examples: 35-45 minutes
- Practice and review: 20-30 minutes

## Key vocabulary

- **Internet**: the worldwide network infrastructure that connects devices and networks.
- **Web**: linked resources transferred mainly through HTTP and viewed with browsers.
- **Client**: software, such as a browser, that requests a resource or service.
- **Server**: software that receives requests and returns responses.
- **URL**: an address that identifies how and where to access a resource.
- **HTTP**: the request-and-response protocol used to transfer web resources.
- **Origin**: the combination of a URL's scheme, host, and port.
- **Media type**: a label, such as `text/html`, describing a response's data format.

## 1.1 Why begin here?

Typing HTML without understanding the Web is like writing an address without knowing what mail is. You may copy the symbols correctly, but you will have no mental model for what happens next. Professional developers use a model of the system to predict where errors might occur.

The **Internet** is a worldwide network of connected computer networks. Many services use it, including email, online games, file transfer, and the **World Wide Web**. The Web is the system of linked resources that browsers request using web addresses.

A **webpage** is one document or resource viewed in a browser. A **website** is a related collection of webpages and supporting files under a common identity or domain. A school's homepage is a webpage; its homepage, admissions pages, news articles, images, and forms together make a website.

## 1.2 Clients and servers

When you visit a page, your browser acts as a **client**: software that asks for a resource. Another computer runs a **server**: software that receives a request and sends a response.

The simplified sequence is:

```text
1. You enter a URL.
2. The browser locates the server.
3. The browser sends an HTTP request.
4. The server sends an HTTP response.
5. The browser interprets the returned files.
6. The browser displays the page.
```

**HTTP** means Hypertext Transfer Protocol. It defines how clients and servers communicate about web resources. HTTPS is HTTP protected by encryption and identity checks.

A response commonly includes HTML. While reading that HTML, the browser may discover references to CSS, JavaScript, fonts, images, video, or other resources and request those too. A visible page may therefore require many request-response exchanges.

> Instructor's note: A server is not necessarily one special physical machine. It is a role performed by software. One computer can run several servers, and a large website can use thousands of machines.

## 1.3 Reading a URL

Consider:

```text
https://example.edu/courses/html/index.html?week=1#exercise
```

| Part | Example | Purpose |
| --- | --- | --- |
| Scheme | `https` | Communication method |
| Host | `example.edu` | Server name |
| Path | `/courses/html/index.html` | Resource location |
| Query | `?week=1` | Extra request data |
| Fragment | `#exercise` | Location inside the returned document |

The fragment is normally handled by the browser and is not needed to choose the resource from the server. You will create fragment links in Chapter 6.

## 1.4 HTML, CSS, and JavaScript

The three core frontend technologies cooperate but solve different problems.

### HTML: structure and meaning

HTML identifies content as a heading, paragraph, navigation area, image, table, form field, and much more.

```html
<h1>Weather Report</h1>
<p>Today will be warm and cloudy.</p>
```

### CSS: presentation

CSS selects HTML and describes appearance and layout.

```css
h1 {
  color: navy;
}
```

### JavaScript: behavior

JavaScript can respond to actions, calculate values, modify a document, and communicate with services.

```javascript
console.log("The page is ready.");
```

HTML is not a programming language: it does not express algorithms with variables, loops, and decisions. It is a **markup language** because it marks content with meaning. That does not make it unimportant. A correct document structure is the foundation on which styling, scripting, accessibility, and search systems depend.

## 1.5 Local and published pages

A **local file** exists on your computer. Its address may begin with `file:///`. Other people cannot normally visit that address because the file is not on their computers.

A **published page** is stored on a host that accepts web requests. It usually has an `https://` address. The HTML language is essentially the same in both places; publishing changes where and how the browser obtains the files.

During this course, you will work locally. That keeps early experiments private, fast, and simple.

## 1.6 Status codes, media types, and origins

An HTTP response contains more than page content. It also carries a **status code** and headers describing the response.

Common status-code groups are:

| Range | General meaning | Familiar example |
| --- | --- | --- |
| `200`–`299` | Successful result | `200 OK` |
| `300`–`399` | Redirection | Resource has another location |
| `400`–`499` | Client-side request problem | `404 Not Found` |
| `500`–`599` | Server-side failure | `500 Internal Server Error` |

The status does not tell the whole story, but it quickly classifies what happened.

A response also identifies its **media type**, historically called a MIME type. HTML served on the Web normally uses:

```text
Content-Type: text/html; charset=UTF-8
```

Other examples include `text/css`, `image/png`, `application/pdf`, and `application/javascript`. Browsers use media types to decide how to process resources. A file named `.html` can still be mishandled if a server sends an inappropriate type.

An **origin** combines a URL's scheme, host, and port:

```text
https://example.org:443
```

Two URLs can share a host but have different origins when their scheme or port differs. Browsers use origins as security boundaries. A local `file:///` page does not behave exactly like a page served from `http://localhost`, especially when later JavaScript requests files or loads modules.

You do not need to configure headers yet. You need to recognize that a response and browser security context contain more information than the HTML source.

## 1.7 Standards, implementations, and references

HTML is a **Living Standard** maintained through ongoing discussion, specification work, browser implementation, testing, and feedback. It is not frozen at a historical label such as “HTML5.”

Different sources answer different questions:

| Source | Best question |
| --- | --- |
| HTML specification | What behavior and authoring rules are defined? |
| Browser implementation | What does this browser actually support? |
| Compatibility data | Which selected browser versions support the feature? |
| Tutorial or textbook | How can a learner understand and apply the feature? |
| Validator | Does this source meet machine-checkable conformance rules? |

These sources cooperate but are not interchangeable. A feature may appear in a specification before every target browser implements it. A browser may recover from invalid source without making that source conforming. A popular tutorial can also be old or incorrect.

When researching an unfamiliar feature:

1. Begin with a maintained reference or the specification.
2. Check current compatibility evidence for your actual audience.
3. Test the simplest example in the target environments.
4. Plan a fallback when missing support would block content or operation.
5. Record the source and date because the platform changes.

## 1.8 Pause and predict

**C01-Q1 - Warm-up.** A browser asks a server for `/about.html`. Which one is the client?

**C01-Q2 - Warm-up.** Match each technology to its primary responsibility:

1. HTML
2. CSS
3. JavaScript

a. behavior  
b. presentation  
c. structure and meaning

**C01-Q3 - Core challenge.** In the URL below, identify the scheme, host, path, and fragment.

```text
https://library.example.org/books/web.html#chapter-2
```

**C01-Q4 - Core challenge.** Put these events in order:

- The server sends a response.
- The browser displays the interpreted document.
- The user enters a URL.
- The browser sends a request.

**C01-Q5 - Spot the misconception.** A student says, “The Internet and the Web are exactly the same thing.” Correct the statement in two sentences.

**C01-Q6 - Classification.** Classify each status as success, redirection, client error, or server error: `200`, `301`, `404`, `503`.

## 1.9 Guided investigation

Open a familiar webpage. Without changing anything:

1. Identify the browser, which is the client.
2. Read the URL and locate its scheme and host.
3. Press `F12` to open Developer Tools.
4. Find the Network panel, then refresh the page.
5. Observe that one visible page can involve many resource requests.

Do not worry about understanding every row. The objective is to connect the abstract request-response model to evidence in your browser.

## 1.10 Stretch challenge: follow one click

Choose one link on the page and describe what you believe happens from the moment you click until the next page appears. Use the terms **client**, **URL**, **request**, **server**, **response**, and **browser**.

There are implementation details you do not know yet. A useful model can be incomplete as long as its known parts are accurate.

## Common misconceptions

- **“Google is the Internet.”** Google operates web services; it is not the network itself.
- **“Every URL ends in `.html`.”** Servers can map many kinds of URL paths to generated or stored resources.
- **“HTML makes a page visually attractive.”** Browsers have default presentation, but deliberate visual design belongs primarily to CSS.
- **“JavaScript is required for every webpage.”** A useful document can work with HTML alone.
- **“Viewing a local file publishes it.”** It remains on your machine until you intentionally host it.

## Chapter summary

The Internet supplies connectivity; the Web supplies linked resources. A browser client requests resources from a server using URLs and HTTP. HTML describes structure and meaning, CSS controls presentation, and JavaScript supplies programmable behavior. You can learn HTML locally before publishing anything.

## Mastery checklist

- [ ] I can define Internet, Web, website, and webpage.
- [ ] I can explain client, request, server, and response in order.
- [ ] I can locate the scheme, host, path, query, and fragment in a URL.
- [ ] I can distinguish HTML, CSS, and JavaScript.
- [ ] I can explain why a local page is not automatically public.
- [ ] I can recognize status-code groups, `text/html`, and an origin.
- [ ] I can explain why a specification, compatibility table, test, and tutorial provide different evidence.

Solutions: [Foundations answer key](../answer-keys/01-foundations.md#chapter-1)

## Authoritative references

- [WHATWG: URLs](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#urls)
- [WHATWG: Loading web pages](https://html.spec.whatwg.org/multipage/browsing-the-web.html)
- [WHATWG FAQ](https://whatwg.org/faq)
- [HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110)

[Next: Chapter 2 - Files, Editors, and Workspaces](02-files-editors-and-workspaces.md)
