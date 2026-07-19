# Chapter 11: Tables and Structured Data

[Course home](../HTML_CRASH_COURSE.md) | [Previous: Semantic Page Structure](10-semantic-page-structure.md) | [Next: Forms and Input Controls](12-forms-and-input-controls.md)

## Prerequisites

- Chapters 1-10
- Tree relationships and semantic structure

## Learning objectives

You will learn to:

- Decide when information is genuinely tabular.
- Create rows, header cells, and data cells.
- Add captions and row/column associations.
- Organize complex tables with row groups and spans.
- Recognize column grouping and explicit complex-header associations.
- Avoid using tables for visual page layout.
- Evaluate a table's accessibility.

## Suggested study time

- Reading and table analysis: 55-70 minutes
- Practice and guided lab: 50-70 minutes

## Key vocabulary

- **Tabular data**: information whose meaning depends on row-and-column relationships.
- **Caption**: a table's identifying title or concise description.
- **Header cell**: a `th` cell that labels related data cells.
- **Data cell**: a `td` cell containing a value in the table.
- **Scope**: an attribute identifying whether a header applies to a row, column, or group.
- **Cell span**: one cell extending across multiple rows or columns.
- **Header association**: the relationship connecting a data cell to the headers that explain it.
- **Column group**: structural metadata describing one or more table columns.

## 11.1 What makes data tabular?

Use a table when values gain meaning from their intersection of rows and columns. A class schedule is tabular because “10:00 AM” means something different under Monday than under Friday.

Do not use a table merely to place a logo beside a paragraph or create columns. That is visual layout and belongs to CSS.

Before writing markup, state:

- What does each row represent?
- What does each column represent?
- What title explains the table's purpose?

If those questions have clear answers, a table may be appropriate.

## 11.2 A basic accessible table

```html
<table>
  <caption>Workshop schedule for August</caption>
  <thead>
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Topic</th>
      <th scope="col">Room</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>August 3</td>
      <td>HTML foundations</td>
      <td>204</td>
    </tr>
    <tr>
      <td>August 10</td>
      <td>Accessible forms</td>
      <td>301</td>
    </tr>
  </tbody>
</table>
```

- `table` contains the tabular data.
- `caption` provides the table's visible title or purpose.
- `tr` creates a table row.
- `th` creates a header cell.
- `td` creates a data cell.
- `thead` groups header rows.
- `tbody` groups primary data rows.
- `scope="col"` tells software that each header applies down its column.

The number of cells should correspond across ordinary rows unless a deliberate span changes the grid.

## 11.3 Row headers

Some tables need row and column headers:

```html
<table>
  <caption>Library opening hours</caption>
  <thead>
    <tr>
      <th scope="col">Day</th>
      <th scope="col">Opens</th>
      <th scope="col">Closes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Monday</th>
      <td>8:00 AM</td>
      <td>6:00 PM</td>
    </tr>
    <tr>
      <th scope="row">Saturday</th>
      <td>9:00 AM</td>
      <td>1:00 PM</td>
    </tr>
  </tbody>
</table>
```

When a screen reader reaches `6:00 PM`, associated headers can communicate “Monday, Closes, 6:00 PM.”

## 11.4 Footers and grouping

`tfoot` groups summary rows:

```html
<tfoot>
  <tr>
    <th scope="row">Total</th>
    <td>42</td>
    <td>38</td>
  </tr>
</tfoot>
```

Row groups communicate structure and provide useful styling hooks later. They do not replace proper header associations.

## 11.5 Spanning cells

`colspan` lets a cell occupy several columns:

```html
<tr>
  <th scope="row">Friday</th>
  <td colspan="2">Campus closed</td>
</tr>
```

`rowspan` lets a cell occupy several rows:

```html
<tr>
  <th rowspan="2" scope="rowgroup">Morning</th>
  <td>8:00</td>
  <td>Registration</td>
</tr>
<tr>
  <td>9:00</td>
  <td>Opening lecture</td>
</tr>
```

Spans change the grid and can make associations harder to understand. Use them only when they accurately model the data. For highly complex tables, explicit `id` and `headers` associations may be needed; simplifying the table is often better.

## 11.6 Captions, surrounding text, and summaries

A concise `caption` identifies the table. Explanations, trends, and instructions belong in normal prose before or after it. The obsolete `summary` attribute must not be used.

```html
<p id="schedule-note">
  All times use Philippine Standard Time. Rooms may change.
</p>
<table aria-describedby="schedule-note">
  <caption>Final examination schedule</caption>
  <!-- Header and data rows omitted for brevity. -->
</table>
```

Use `aria-describedby` only when associating the extra explanation is genuinely helpful; visible prose remains available to everyone.

## 11.7 Column groups

`colgroup` and `col` describe columns primarily so later CSS can apply shared presentation:

```html
<table>
  <caption>Course enrollment</caption>
  <colgroup>
    <col>
    <col span="2" class="enrollment-count">
  </colgroup>
  <!-- Header and data rows omitted for brevity. -->
</table>
```

This declares one first column and a two-column group. It does not replace `th`, `scope`, or other header associations. Do not add column markup when it serves no purpose.

## 11.8 Complex header associations

Simple tables should use `scope="col"` and `scope="row"`. When a genuinely complex table has multi-level headers, `id` and `headers` can make associations explicit:

```html
<table>
  <caption>Workshop attendance</caption>
  <colgroup>
    <col>
  </colgroup>
  <colgroup span="2"></colgroup>
  <thead>
    <tr>
      <th rowspan="2" id="region" scope="col">Region</th>
      <th colspan="2" id="attendance" scope="colgroup">
        Attendance
      </th>
    </tr>
    <tr>
      <th id="morning" headers="attendance" scope="col">Morning</th>
      <th id="afternoon" headers="attendance" scope="col">Afternoon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="north" headers="region" scope="row">North</th>
      <td headers="north attendance morning">42</td>
      <td headers="north attendance afternoon">38</td>
    </tr>
  </tbody>
</table>
```

Each `headers` value is a space-separated list of header-cell IDs relevant to that cell.

Before building this complexity, ask whether two smaller tables or a simpler data design would be easier to understand. Test complex tables with actual assistive technologies; correct-looking source does not guarantee a clear reading experience.

## 11.9 Practice

**C11-Q1 - Semantic choice.** Should a two-column visual page layout use a table? Why?

**C11-Q2 - Fill in the blanks.**

```html
<table>
  <_______>Course results</_______>
  <tr>
    <__ scope="col">Student</__>
    <__ scope="col">Score</__>
  </tr>
</table>
```

**C11-Q3 - Association puzzle.** What does `scope="row"` say about a header cell?

**C11-Q4 - Grid puzzle.** A row has one `td colspan="2"` plus one ordinary `td`. How many columns does it occupy?

**C11-Q5 - Spot the problem.** What important context is missing?

```html
<table>
  <tr><td>Monday</td><td>8:00</td></tr>
</table>
```

**C11-Q6 - Core challenge.** Write a two-column table with caption, column headers, and two data rows.

**C11-Q7 - Semantic choice.** Should a day name that labels its entire row use `td` or `th scope="row"`?

**C11-Q8 - Complexity decision.** What should you try before adding long `headers` lists to a difficult table, and what element remains necessary even when `colgroup` is present?

## Guided lab: study schedule

Create an accessible weekly schedule:

1. Add a specific caption.
2. Use column headings for day, start time, topic, and location.
3. Use at least three data rows.
4. Make the day a row header if it uniquely labels each row.
5. Group header and body rows.
6. Read each data cell aloud with the headers that give it meaning.

## Stretch challenge: normalize confusing data

A student creates one enormous table containing course information, teacher biographies, paragraphs of policies, and a weekly schedule. Divide the information into semantic prose and one or more focused tables. Explain which information truly depends on row-column intersections.

## Common misconceptions

- Tables describe data relationships, not screen layout.
- `th` is defined by its header role, not bold appearance.
- A caption is the table's title, not an explanation of every trend.
- `thead`, `tbody`, and `tfoot` group rows; they do not automatically create header associations.
- Spans are not harmless decoration; they alter the logical grid.

## Chapter summary

Tables model data through row and column intersections. Captions state purpose, `th` cells identify headers, and `scope` communicates associations. Row groups organize structure, while spans model genuine shared cells. Simpler, well-labeled tables are easier for everyone to understand.

## Mastery checklist

- [ ] I can decide whether data is tabular.
- [ ] I can create a captioned table with headers and data.
- [ ] I can mark row and column headers.
- [ ] I understand row groups and spans.
- [ ] I do not use tables for layout.
- [ ] I can verbally associate each data cell with its headers.
- [ ] I understand the limited role of `colgroup` and when explicit `headers` may be needed.

Solutions: [Media, structure, and tables answer key](../answer-keys/03-media-structure-and-tables.md#chapter-11)

## Authoritative references

- [WHATWG: Tables](https://html.spec.whatwg.org/multipage/tables.html)
- [W3C WAI: Tables tutorial](https://www.w3.org/WAI/tutorials/tables/)

[Next: Chapter 12 - Forms and Input Controls](12-forms-and-input-controls.md)
