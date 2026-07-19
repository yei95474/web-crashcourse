# Debugging Checklist

[Course home](../HTML_CRASH_COURSE.md) | [Chapter 18](../chapters/18-debugging-testing-and-validation.md)

Use this checklist from top to bottom. Check one hypothesis at a time.

## Establish the symptom

- [ ] Name the exact page and action.
- [ ] State the expected result.
- [ ] State the actual result.
- [ ] Reproduce the problem twice.
- [ ] Note the browser and whether the page is local or served.

## Confirm the active file

- [ ] Save all relevant files.
- [ ] Refresh the correct tab.
- [ ] Compare the browser address with the file you edited.
- [ ] Check for duplicate copies of the project.
- [ ] Confirm the full extension is `.html`, not `.html.txt`.
- [ ] Record whether the page uses `file:`, local HTTP, or production HTTPS.

## Check paths

- [ ] Draw the project directory tree.
- [ ] Begin calculation from the current HTML file.
- [ ] Match every filename's spelling, case, and extension.
- [ ] Use `/` in web paths.
- [ ] Move up with one `../` per parent directory.
- [ ] Avoid local absolute paths such as `C:\Users\...`.
- [ ] Inspect the computed URL in the browser Network panel.

## Check syntax and structure

- [ ] Confirm the doctype and document skeleton.
- [ ] Match opening and closing tags.
- [ ] Close nested elements in reverse order.
- [ ] Remove duplicate attributes.
- [ ] Confirm void elements have no closing tags or children.
- [ ] Check quotation marks around attribute values.
- [ ] Verify parent-child rules.
- [ ] Search for duplicate IDs.

## Check semantics and accessibility

- [ ] Confirm headings form a logical hierarchy.
- [ ] Confirm each page has one clear main content area.
- [ ] Check link names out of context.
- [ ] Review every image's alt decision.
- [ ] Associate table data with headers.
- [ ] Match every form label `for` to a unique control `id`.
- [ ] Group radio and checkbox questions with `fieldset` and `legend`.
- [ ] Operate the page with a keyboard.

## Use evidence

- [ ] Inspect the parsed tree in Developer Tools.
- [ ] Check the Network panel for failed resources.
- [ ] Record the requested URL, status, and `Content-Type`.
- [ ] Read relevant Console messages.
- [ ] Inspect accessible names and roles.
- [ ] Validate the HTML and fix the earliest structural error first.
- [ ] Compare source with the browser's parsed DOM.
- [ ] Check current compatibility information for an unfamiliar required feature.

## Isolate

- [ ] Reproduce the issue in the smallest possible fragment.
- [ ] Temporarily remove unrelated markup.
- [ ] Change one variable.
- [ ] Write the expected result of that change.
- [ ] Undo experiments that did not solve the cause.

## Verify the repair

- [ ] Reproduce the original steps.
- [ ] Confirm the expected result.
- [ ] Test neighboring pages and paths.
- [ ] Test keyboard and zoom behavior.
- [ ] Validate again.
- [ ] Record the cause and prevention.

## Defect record template

```text
ID:
Page/environment:
Action:
Expected:
Actual:
Evidence:
Cause:
Repair:
Retest:
Related risk:
Environment and versions:
Status/content type:
```
