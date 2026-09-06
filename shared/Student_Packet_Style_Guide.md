# Student Packet Style Guide (v1.2)

Shared, cross-modality Section 3 ("Format and Style Constraints") for every lesson type's Student
Packet / Student Print Formatting prompt. Each modality's own packet-generation prompt should not
carry its own copy of this content - it should point here (paste this file alongside the modality
prompt when generating) and add only what's genuinely specific to that modality: new CSS classes
for structural elements this file's base stylesheet doesn't cover (see "Extending this stylesheet"
below).

This exists because, before it did, the only complete copy of this material lived inside Passage
Reading's own packet prompt, and the other modalities either cross-referenced it by prose (fragile:
no mechanical link, so a change there had no way to reach the modalities pointing at it) or lacked
it entirely. See `Changelog.md` for what changed when it was extracted.

## A. Universal format constraints

### A.1 Single self-contained HTML file

Produce one HTML file with all CSS embedded in a `<style>` block in the head and no external
resources (fonts, scripts, images) other than a simple browser print trigger (`window.print()` on
an on-screen button hidden via `@media print`). This is what makes the document reliably printable
directly from a browser without setup.

### A.2 Black and white only

Design for black-and-white printing exclusively: no color-dependent meaning anywhere in the layout
(star counts, not color, indicate difficulty; borders and typographic weight, not color,
distinguish content types). Use a pure black/white/gray palette.

### A.3 No em-dashes

Never use em-dashes anywhere in the generated document. Use standard hyphens, colons, or
parentheses instead, consistent with the lesson type's own Lesson Generation Prompt's constraint.

### A.4 Print-safe layout

Use `page-break-inside:avoid` / `break-inside:avoid` (or the modern equivalent) on content blocks
that should not split awkwardly across a printed page: callout boxes, task blocks, individual
questions/items with their answer lines, and reused/refresher text blocks.

## B. Base stylesheet

The required starting point for every packet, across every modality: reuse it as-is. A modality's
own packet prompt may add a new class only where a structural element genuinely isn't covered here
(see "Extending this stylesheet" below) - never restyle an existing element's fonts, colors, or
spacing on its own judgment.

```css
:root {
  --ink: #000000;
  --ink-soft: #333333;
  --paper: #ffffff;
  --rule: #999999;
  --rule-light: #cccccc;
}
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  background: #e8e8e8;
  color: var(--ink);
  font-family: Georgia, "Iowan Old Style", "Palatino Linotype", serif;
  line-height: 1.55;
}
.sheet {
  max-width: 820px;
  margin: 0 auto;
  background: var(--paper);
  padding: 48px 40px 60px;
}
.toolbar {
  max-width: 820px;
  margin: 0 auto;
  padding: 14px 40px 0;
  display: flex;
  justify-content: flex-end;
}
.print-btn {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  padding: 8px 16px;
  background: #000;
  color: #fff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
.print-btn:hover {
  background: #333;
}

h1,
h2,
h3 {
  font-family: "Iowan Old Style", Georgia, serif;
  margin: 0;
  color: var(--ink);
}
.masthead {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 16px;
  text-align: left;
  margin-bottom: 20px;
}
.masthead h1 {
  font-size: 26px;
  margin-bottom: 6px;
}
.masthead + .masthead,
.masthead.masthead-later {
  margin-top: 60px;
}
.masthead-tag {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--ink);
  white-space: nowrap;
  margin-top: 4px;
}

.objective {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
  color: var(--ink);
  margin: 0 0 24px;
}
.objective strong {
  font-weight: 700;
}

.section-title {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12.5px;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--ink);
  font-weight: 700;
  margin: 32px 0 10px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.section-title::after {
  content: "";
  flex: 1;
  height: 1px;
  background: var(--rule-light);
}

.exercise-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  font-weight: 700;
  color: var(--ink);
}
.instr-inline {
  margin-top: 20px;
}
.instr-inline .exercise-label {
  margin-right: 6px;
}

.section-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  font-weight: 700;
  font-style: italic;
  color: var(--ink);
  margin: 20px 0 8px;
}

p {
  margin: 0 0 12px;
}
.instr {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14.5px;
  color: var(--ink);
}

.spotlight-box {
  border: 1px solid var(--ink);
  padding: 16px 20px;
  margin: 14px 0;
  page-break-inside: avoid;
  break-inside: avoid;
}
.spotlight-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 11.5px;
  letter-spacing: .08em;
  text-transform: uppercase;
  font-weight: 700;
  margin-bottom: 8px;
}
.model-step {
  font-size: 14px;
  margin-bottom: 10px;
}
.model-step:last-child {
  margin-bottom: 0;
}
.model-step strong {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12.5px;
  letter-spacing: .03em;
}

.vocab-list {
  margin: 10px 0 6px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
}
.vocab-list .vrow {
  display: flex;
  gap: 10px;
  padding: 6px 0;
  border-bottom: 1px solid var(--rule-light);
}
.vocab-list .vrow:last-child {
  border-bottom: none;
}
.vocab-list .word {
  font-family: Georgia, serif;
  font-style: italic;
  font-weight: 700;
  white-space: nowrap;
  min-width: 130px;
}

.idiom-item {
  margin-bottom: 10px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
}
.idiom-item:last-child {
  margin-bottom: 0;
}
.idiom-phrase {
  font-family: Georgia, serif;
  font-weight: 700;
  font-style: italic;
}

.annot-key {
  float: right;
  width: 190px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 11.5px;
  margin: 2px 0 12px 20px;
  padding: 12px 14px;
  border: 1px solid var(--ink);
}
.annot-key-title {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: .06em;
  text-transform: uppercase;
  text-align: center;
  margin-bottom: 8px;
}
.annot-key .k-row {
  margin: 7px 0;
}
.annot-key .k-mark {
  font-family: Georgia, serif;
  font-weight: 700;
  display: block;
}
.clearfloat {
  clear: both;
}

.image-placeholder {
  border: 2px dashed var(--ink);
  padding: 44px 20px;
  text-align: center;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  color: var(--ink-soft);
  margin: 14px 0 4px;
}
.image-caption {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-style: italic;
  color: var(--ink-soft);
  text-align: center;
  margin: 0 0 20px;
}

.article {
  padding: 6px 0 0;
  margin: 18px 0 22px;
}
.article .headline {
  font-size: 22px;
  font-weight: 700;
  text-align: center;
  margin: 20px 0 4px;
}
.article .byline {
  text-align: center;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 11px;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--ink-soft);
  margin-bottom: 20px;
}
.article p {
  font-size: 15.5px;
  margin-bottom: 14px;
  page-break-inside: avoid;
  break-inside: avoid;
}
.para-letter {
  font-weight: 700;
  margin-right: 2px;
}
.footref {
  font-weight: 700;
}
.idiom-mark {
  text-decoration: underline dotted var(--ink);
  text-decoration-thickness: 1.5px;
}
.article .footnotes {
  margin-top: 22px;
  padding: 14px 0 22px;
  border-top: 1px solid var(--rule-light);
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  color: var(--ink-soft);
}
.article .footnotes div {
  margin-bottom: 6px;
}

.qlist {
  margin: 0;
  padding-left: 0;
  list-style: none;
}
.qlist li {
  display: flex;
  gap: 10px;
  margin-bottom: 11px;
  font-size: 14.5px;
}
.num {
  font-family: system-ui, -apple-system, sans-serif;
  font-weight: 700;
  flex-shrink: 0;
  width: 20px;
}
.qlist .blank {
  display: inline-block;
  border-bottom: 1px solid var(--ink-soft);
  min-width: 70px;
}
.qbody {
  flex: 1;
}
.ans-line {
  display: block;
  border-bottom: 1px solid var(--ink-soft);
  height: 22px;
  margin-top: 4px;
}
.ans-line-sm {
  display: inline-block;
  border-bottom: 1px solid var(--ink-soft);
  width: 100%;
  max-width: 320px;
  height: 18px;
  margin-top: 2px;
}

.subgroup-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-weight: 700;
  font-style: italic;
  color: var(--ink);
  margin: 14px 0 8px;
}

.fillblank {
  margin: 0;
  padding-left: 0;
  list-style: none;
}
.fillblank li {
  margin-bottom: 9px;
  font-size: 14.5px;
}
.fillblank .num {
  font-family: system-ui, -apple-system, sans-serif;
  font-weight: 700;
  margin-right: 8px;
}

.refresher {
  padding: 16px 0;
  margin: 14px 0;
  border-bottom: 1px solid var(--rule-light);
}
.refresher.refresher-noline {
  border-bottom: none;
}
.refresher .headline {
  font-size: 17px;
  font-weight: 700;
  margin-bottom: 12px;
  text-align: center;
}
.refresher p {
  font-size: 14.5px;
}

.task-block {
  margin: 18px 0 22px;
  page-break-inside: avoid;
  break-inside: avoid;
}
.task-block .stars {
  font-size: 16px;
  letter-spacing: 2px;
}
.task-block p,
.task-block li {
  font-size: 14.5px;
}
.task-block .instr-line {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14.5px;
  color: var(--ink);
  margin-bottom: 10px;
}
.task-block .instr-line .exercise-label {
  margin-right: 2px;
}
.task-block .instr-line .stars {
  margin-right: 8px;
}
.wordbank {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  padding: 8px 0;
  margin: 10px 0;
  border-top: 1px dashed var(--rule-light);
  border-bottom: 1px dashed var(--rule-light);
}
.task-block .starter {
  font-style: italic;
  padding: 8px 0 8px 14px;
  margin: 10px 0;
  border-left: 3px solid var(--ink);
  font-size: 14px;
}

.discuss-block {
  margin: 16px 0;
}
.stems {
  margin: 0;
  padding-left: 0;
  list-style: none;
}
.stems li {
  display: flex;
  gap: 10px;
  align-items: baseline;
  margin-bottom: 9px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.stems .stars {
  font-size: 13px;
  flex-shrink: 0;
  width: 52px;
  letter-spacing: 1px;
}

.wrapup {
  margin: 16px 0;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
}

@media print {
  body {
    background: #fff;
  }
  .toolbar {
    display: none;
  }
  .sheet {
    padding: 0 12px;
    max-width: 100%;
  }
  .spotlight-box,
  .task-block,
  .article p,
  .refresher,
  .discuss-block,
  .wrapup,
  .article {
    page-break-inside: avoid;
    break-inside: avoid;
  }
}
```

The document's opening masthead (only - never a later `.masthead.masthead-later` heading) includes
exactly one `<span class="masthead-tag">` alongside the `h1`, holding that modality's plain class
label (`Reading`, `Listening & Speaking`, or `Writing` - see each lesson type's own Student Packet
prompt §2.4 for which one). This is a distinct, newly-defined element for a specific purpose (a
quick visual identifier for whoever is handling the printed packet), not a revival of `.kicker` or
`.sub`: those belonged to a masthead subtitle line no current lesson type's Section 2 uses, and a
fresh document should still not define or carry them forward.

## C. HTML markup conventions

Applies to every packet's own document skeleton and to the CSS inside its `<style>` block, so
packets converge on one look in view-source regardless of which prompt or session generated them:

- **Indentation.** Two spaces per nesting level, consistently, from `<html>` down through `<head>`'s
  children and every rule inside `<style>`.
- **Void elements self-close with a space:** `<meta charset="utf-8" />`, `<br />` - not
  `<meta charset="utf-8">` / `<br>`.
- **CSS rule formatting:** selector(s) then a space then the opening brace, each declaration on its
  own line (`property: value;`, space after the colon), closing brace on its own line - even for a
  single-declaration rule. Do not collapse a rule to one line.
- **Multiple selectors sharing one rule** each get their own line, e.g.:
  ```css
  .task-block p,
  .task-block li {
    font-size: 14.5px;
  }
  ```
- **Multi-value properties** (`font-family` and similar) stay on one line, comma-and-space
  separated, rather than one value per line - keeps a simple stack like
  `system-ui, -apple-system, sans-serif` from costing three lines for no readability gain.
- **Quoted CSS values** (a font name with a space in it, `content: ""`) use double quotes, matching
  the double quotes already used for every HTML attribute.

Example skeleton showing the doctype/head conventions together (body/style contents omitted):

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Lesson Title: Student Packet</title>
    <style>
      :root {
        --ink: #000000;
        ...
      }
    </style>
  </head>
  <body>
    ...
  </body>
</html>
```

## D. Extending this stylesheet

A modality's own packet prompt may add new CSS classes only for structural elements genuinely not
covered by the base stylesheet above (a citation box, a fillable table, a picture placeholder grid -
whatever that modality's document structure needs that no existing class already provides). Follow
the same rule formatting (§C) when writing new classes. Never restyle an existing base class's
fonts, colors, or spacing - if an existing class's look needs to change, that change belongs in this
shared file (updating it for every modality at once), not as a modality-local override.

## Changelog

**Current version: v1.2.** For the full dated version history and the reasoning behind each
change, see `Changelog.md`.
