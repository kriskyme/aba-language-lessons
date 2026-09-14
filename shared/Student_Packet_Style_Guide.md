# Student Packet Style Guide (v2.48)

Shared, cross-modality rules for every lesson type's Student Packet and Assessment Student Packet
prompt: the universal format constraints (§A), the base stylesheet (§B), markup conventions (§C), how
a modality extends the stylesheet (§D) and the per-modality delta classes themselves (§H), the
teacher-to-student translations every packet applies (§E), star-rating and lettered-Task rules (§F),
the rule that a packet is always a regeneration of its Markdown source (§G), and the shared packet
self-check (§I). Paste this file alongside the modality's packet prompt when generating. A modality's
own packet prompt does not restate anything here and never cites another modality's prompt for a
rule - it points to the section here and adds only what is specific to its own document structure.
See `Changelog.md` for history.

## A. Universal format constraints

### A.1 Single self-contained HTML file

Produce one HTML file with all CSS embedded in a `<style>` block in the head and no external
resources (fonts, scripts, images) other than a simple browser print trigger (`window.print()` on
an on-screen button hidden via `@media print`). This is what makes the document reliably printable
directly from a browser without setup. An image is embedded inline as a base64 data URI in the `<img>`'s
`src`; never a `src` that points at a file, even one in the same folder.

### A.2 Black and white only

Design for black-and-white printing exclusively: no color-dependent meaning anywhere in the layout
(star counts, not color, indicate difficulty; borders and typographic weight, not color,
distinguish content types). Use a pure black/white/gray palette.

**No item is answered by reading a chromatic color off a printed picture.** The rule above is about
the packet's own design; this one is about its content, and it binds the lesson document as much as
the packet, because the packet is where the task is finally answered. An embedded photograph prints
in grayscale, so an item asking which picture is red, a word bank offering *orange* and *blue* as
answers about a photograph, or an expected answer of "It is orange." cannot be settled from the
printed page. Where an objective calls for matching a described feature to a picture (the CSV's
Level 1-3 rows, whose own examples use color), build the item on a feature that survives grayscale:
size, shape, quantity, texture, pattern, or the weather or setting of a scene.

Two things this does **not** forbid. **Black, white, and gray survive grayscale** and are legitimate
answers about a printed picture: a black cat, a white hat, and a black-and-white cat stay
distinguishable in print. And a task in which the student **describes their own belonging** may use
any color, because they answer from what they know of the object, not from anything printed. Color
words may also appear freely in an anchor text, a vocabulary list, a word bank whose answers lie
elsewhere, or a spoken task. The prohibition is narrow: a chromatic color as the thing a printed
picture is supposed to tell the student.

### A.3 No em-dashes

Never use em-dashes anywhere in the generated document. Use standard hyphens, colons, or
parentheses instead, consistent with the lesson type's own Lesson Generation Prompt's constraint.

### A.4 Print-safe layout

Use `page-break-inside:avoid` / `break-inside:avoid` (or the modern equivalent) on content blocks
that should not split awkwardly across a printed page: callout boxes, task blocks, individual
questions/items with their answer lines, and reused/refresher text blocks.

## B. Base stylesheet

The required starting point for every packet, across every modality: paste every rule below into the
packet's `<style>`, in full, whether or not this packet uses it. A packet's `<style>` is never a subset
of this block, so a rule a later edit needs (an embedded photo, a second Task shape) is already there. A modality's
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
  line-height: 1.2;
  margin-bottom: 0;
}
.masthead + .masthead,
.masthead.masthead-later {
  margin-top: 60px;
  page-break-before: always;
  break-before: page;
}
.masthead-meta {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 2px;
  margin-top: 0;
  padding-top: 4px;
}
.masthead-tag {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-weight: 700;
  line-height: 1.25;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--ink);
  white-space: nowrap;
}
.masthead-sep {
  font-weight: 400;
  color: var(--rule);
  padding: 0 3px;
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
```

The paragraph always opens with a bold `Objective:` label before the can-do sentence itself, which is
written in the student's voice as "I can" plus the skill (`<p class="objective"><strong>Objective:</strong>
I can describe...</p>`; form in §E) - every modality's packets follow this, so a generation prompt that
produces an unlabeled `.objective` paragraph, or one that opens "You will," "To describe," or a bare
verb, is producing wrong output, not a stylistic variant.

```css

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
  width: 165px;
  flex-shrink: 0;
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
  /* a box the STUDENT draws in ("Draw your phone case here"); never a box the teacher must fill with a photo */
  border: 2px dashed var(--ink);
  padding: 44px 20px;
  text-align: center;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  color: var(--ink-soft);
  margin: 14px 0 4px;
}
.photo {
  /* an embedded image (base64 data URI); sized by this rule, never per packet */
  display: block;
  max-width: 100%;
  height: auto;
  max-height: 300px;
  margin: 14px auto 4px;
}
.image-caption {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-style: italic;
  color: var(--ink-soft);
  text-align: center;
  margin: 0 0 20px;
}

/* Picture-choice items (§F). Base, not a modality delta: any modality whose objective
   ends in matching something to a picture needs these. */
.pic-options {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  margin: 8px 0 4px 4px;
}
.pic-option {
  width: 110px;
}
.pic-option .pic-box {
  /* holds an embedded <img>; never printed empty for the teacher to fill */
  border: 1px solid var(--ink);
  height: 70px;
  padding: 0;
  overflow: hidden;
}
.pic-option .pic-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.pic-option .pic-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12.5px;
  text-align: center;
  margin-top: 5px;
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
.byline {
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
  font-size: 0.72em;
  vertical-align: super;
  line-height: 0;
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

/* Matching items and the two-source compare layout (§F). Base, not a modality delta:
   any modality that prints two sources to compare needs these. */
.match-list {
  margin: 8px 0 4px 4px;
}
.match-row {
  margin-bottom: 14px;
}
.match-row .match-label {
  display: block;
  font-weight: 700;
  margin-bottom: 3px;
}
.match-row .match-src {
  display: block;
  margin: 0 0 5px 12px;
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
.qbody {
  flex: 1;
}

/* `.blank` and `.ans-line`/`.ans-line-sm` are not interchangeable. `.blank` is a short
   blank that sits INSIDE a sentence, mid-line, under any list wrapper (`.qlist`,
   `.fillblank`, or none) - e.g. "My case is <span class="blank"></span> (thick).".
   `.ans-line` / `.ans-line-sm` is a standalone full-width line by itself BELOW a prompt,
   for writing a full answer - never place either one mid-sentence, and never use
   `.ans-line-sm` where you mean `.blank`. */
.blank {
  display: inline-block;
  border-bottom: 1px solid var(--ink-soft);
  min-width: 70px;
}
.ans-line {
  display: block;
  border-bottom: 1px solid var(--ink-soft);
  height: 22px;
  margin-top: 4px;
}
.ans-line-sm {
  display: block;
  border-bottom: 1px solid var(--ink-soft);
  width: 100%;
  height: 18px;
  margin-top: 2px;
}

/* `.editable` opens the leading of printed text a task asks the student to write into or
   above (a Fix the Wrong Word line, a Check What You Heard line). Put it on the list or
   the block that holds that text, never on ordinary reading text. A printed paragraph of
   several lines is not annotated between the lines at all - see §F, "Writing on printed
   text." */
.editable {
  line-height: 2.5;
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
/* .wordbank holds plain inline text only: a bold label, then items separated by " &middot; ".
   A single-list bank is one line: <strong>Word bank:</strong> a &middot; b &middot; c
   A grouped bank is one <strong>Group:</strong> line per group, lines joined by <br />.
   Never wrap its lines in <p>, .model-step, or any other class (see §F, Word banks). */
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
.discuss-block .prompt {
  font-size: 14.5px;
  margin: 10px 0 16px;
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

Every masthead in the document - the opening `.masthead` and each later
`.masthead.masthead-later` - includes a `<div class="masthead-meta">` alongside its `h1`, with
identical content in each, so a Unit _B page (which always starts its own printed sheet) identifies
itself as fully as page 1 does. The stack holds exactly two `<span class="masthead-tag">` lines:

1. That modality's plain class label (`Reading`, `Listening & Speaking`, or `Writing` - see each
   lesson type's own Student Packet prompt §2.4 for which one), then
   `<span class="masthead-sep">&#183;</span>`, then the lesson's Module name plain and unprefixed
   (`Describing`, `Narrating`, ...), spelled exactly as `Program_Conventions.md` §A names it. The
   Module's name, never its number: the version code on the next line already carries the number,
   and the name is what stays readable if Modules are ever reordered.
2. The lesson's Band and its version code, combined as one space-separated string:
   `<Band> <Module>.<Set>.<Lesson>.<Version>` (e.g. `Advanced 1.1.1.0`). Band is plain language
   (`Beginner`, `Intermediate`, `Advanced`, or `Proficient`); the version code format is defined in
   `Program_Conventions.md` §G - the lesson number in it is the global one from
   `Program_Conventions.md` §C, not restarted per Set. A lesson that is unversioned by design
   carries the Band alone.

Two lines, not one per fact: three stacked tags made the meta block the tallest thing in the
masthead, pushing the lesson's first content down the page.

```html
<div class="masthead">
  <h1>Unit 3A: Saving the Key Deer</h1>
  <div class="masthead-meta">
    <span class="masthead-tag">Listening &amp; Speaking <span class="masthead-sep">&#183;</span> Describing</span>
    <span class="masthead-tag">Advanced 1.1.3.1</span>
  </div>
</div>
```

Nothing else sits on that stack (no "Class" or "Packet" suffix), and nowhere else in the document
is there a Name/Date field, a subject/module kicker line, a subtitle line under any heading, or a
footer note. Do not define or carry forward `.kicker`/`.sub`.

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
- **Footnote references** are `<span class="footref">1</span>` with a plain ASCII digit, immediately after the
  word with no space before it, and the matching note in the `.footnotes` footer opens with the same digit and a
  full stop. The raised position comes from the `.footref` rule in §B, never from the markup: do not wrap it in
  `<sup>` (which raises it a second time on top of the CSS) and do not type a Unicode superscript character
  (`¹`, `²`), which cannot be styled, is unevenly covered across print fonts, and will not match the footer's
  own numeral. One form everywhere, so a reference looks identical in every modality's packet.
- **Quoted CSS values** (a font name with a space in it, `content: ""`) use double quotes, matching
  the double quotes already used for every HTML attribute.
- **A reference list of paired items is a table, never a prose run.** Any student-facing list of
  pairs - base form to past form, word to meaning, term to example, expression to the moment it is
  used - prints as the modality's table class (`.rule-table` §H.3, `.notes-table` §H.1) with a header
  row naming both columns, not as a comma-separated run of pairs inside a `<p>`, `.model-step`, or
  word bank. A list students copy forms out of has to be scannable down a column; a prose run is the
  hardest shape to read on the page and is worse still directly beneath a bordered table, which is
  what it gets compared against. Short pairs may be laid two across (`Now | Past | Now | Past`) to
  halve the row count and keep the table inside one page break. A bank of single words with no
  pairing stays a word bank (§F).

Head fragment showing the doctype/meta conventions together:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Lesson Title: Student Packet</title>
    <style>...</style>
  </head>
```

## D. Extending this stylesheet

A modality may add new CSS classes only for structural elements genuinely not covered by the base
stylesheet above (a citation box, a fillable table, a picture grid - whatever that
modality's document structure needs that no existing class already provides). Those classes live in
§H of this file, under the modality's own heading, following the same rule formatting (§C) - not
inline in the modality's packet prompt, so one paste covers every modality and a fix to a delta
class lands once. Never restyle an existing base class's fonts, colors, or spacing - if an existing
class's look needs to change, that change belongs in §B (updating it for every modality at once),
not as a modality-local override. The type scale is fixed: every student-facing reading line
(instruction, question, discussion prompt, Task item, article body) is the one 14.5px body size, and
only the named display and label classes §B already defines (masthead, section titles and labels,
captions, stems, footnotes, the Task label) carry a different size. A packet never introduces a
selector §B or §H doesn't define, and never gives a section its own size or weight for emphasis.

## E. Universal teacher-to-student translations

Every packet passes this translation before anything else: no term in the left column appears in the
student-facing document. Replace each with the plain-language instruction that tells the student what
to do, silently, without narrating the pedagogy behind it. A modality's packet prompt adds only its own
medium-specific rows (a reading strategy, a segment cue, a grammar focus label); it does not repeat
these.

| Teacher-facing term | Student-facing translation |
|---|---|
| Task Level / Level (numeric); tier, regime, or Level names of any kind | A star rating (★ to ★★★★, more stars = more challenging), with no numeric Level and no tier name ("Foundation," "Extension," "beginner," "warm-up," etc.). See §F. |
| Skill Spotlight | A can-do statement in the student's own voice near the start of the packet, mirroring the `learningobjectives.csv` row's "Can ..." form: "I can" plus the skill, with "my" or "me" where the sentence refers to the student ("Objective: I can describe something of my own by comparing it to something else and giving a real reason for the comparison."). Never "You will," "To describe," a bare verb phrase ("describe..."), or "today we are practicing X." One sentence naming the skill, not the lesson's object or text ("something of my own," never "my phone case"), identical for every student: never "Some of you will also," "if you are at," or any tier narration (Quality Standards §D1). |
| Closing Transfer Check | A plain closing-activity instruction stating what to pick and what to do with it, never named as a check and never referencing assessment or evidence language, and with no stage directions about what the teacher will do next. |
| Fishbowl / Town Hall / Concentric Circles / Jigsaw / discussion carousel / Four Corners / gallery walk / Stand Up-Move | A plain instruction for the protocol's room-neutral form (Quality Standards §D11), never the protocol's name and never a room setup. Rotating Partners prints as find-a-new-partner-as-you-go ("When you finish a question, find a new partner and go on to the next one"); a Panel Round prints the listener's own task; Town Hall, Jigsaw, and small-group discussion print as get into a group, here are your questions, take turns talking. Fold any tracking or listening task into a student's own task rather than dropping it. |
| Activation hooks by name (Visual Inquiry, Take a Side, Mystery Quote, K-W-L Chart, and any retired formation such as K-W-L Walk, Stand Up/Move, or Four Corners) | The plain instruction the activity produces (a warm-up question, a prompt to discuss), never the activity's name - in headings included. The hook's orienting sentence is not a teacher-facing term and is always printed: the student page states the topic before its first question (Quality Standards §D13). |
| Frame / sentence frame / fixed frame / two-slot frame ("complete the frame," "say the frame," "use these frames," "not a memorized frame") | **Sentence.** "Complete the sentence," "Say the sentence," "Use these sentences," "Write your sentence three times." A frame is a teaching device, and the student's job is to finish a sentence; naming the device teaches nothing and a student who asks what a frame is gets a lesson in pedagogy instead of an answer. The word survives only where it is the content: a backpack's internal frame, a loom's wooden frame, the verb ("how the report frames the story"). "Frame" stays in the lesson `.md`, which is the teacher's document, and in this guide. |
| Internal item labels (STOP & CHECK, Fact Finder, the native-Level item set's own name, controlled-practice type names) | Ordinary numbered or lettered questions with no internal label carried into student view. |
| Board-dependent moment | Not shown to students at all; teacher-only classroom-management instruction. |
| Metalanguage for the skill being taught: **time connectors**, sequence markers, transition words, discourse markers, cohesive devices, signposting, topic sentence, hedging | Not printed as a label. Name what the words **do**, in the student's own terms: "the words that tell you when," "your own words to show when each thing happened," "the sentence that says what the paragraph is about." The failure this catches is not a whole packet written in jargon - it is **one** surviving instance. The term gets paraphrased everywhere the page was written carefully and then appears, unglossed, in a single task, usually the highest tier, because that tier's CSV row is phrased in it and the row got copied into the stem. The student meets a named category once, having been taught the thing under a different name or no name, and has no way to tell whether it means something new. So the check is a count, not a read: grep the term across the finished packet, and if it appears at all, either every instance is plain or the term is genuinely taught on the page first. Teaching it is a real option at the upper Bands, but then it is introduced where the skill is introduced and used consistently after - never named once in isolation. The teacher-side Markdown keeps whatever term it likes; this row is about the printed page. |
| Delivery mechanics: who presses play and when it stops ("your teacher will stop the audio partway through," "your teacher will play two parts of it"), and how long a beat lasts ("you will have about half a minute to write," "you have five minutes for this") | Not printed. Delivery is teacher-led facilitation, not page content, and a time allowance printed on the page is a clock the student cannot see and the teacher will override anyway. The page states what the student does with it, not what will be done to them. **What survives the cut** is anything the task itself turns on, said in the student's own experience rather than as teacher action: "You will hear two parts of it," "You will hear the first part of it," "You will hear the story again later, all the way to the end." Where the page already prints the parts and their times, even that is redundant and the instruction is just the student's job: "Fill in only the box for the part you have just heard." |
| The lesson's staging narrated back at the student: what they do now, what happens after that, what they will come back to and change ("answer it from what you heard the first time, before anything is played again. Then you will hear the whole story once more and change any answer you now hear differently, ticking the ones that moved") | Not printed. This is the same fault as delivery mechanics one row up, one level out: not who presses play, but the **teaching protocol** - a commit beat, a second pass, a revise beat - written out as a script the student reads before doing any of it. The staging is the teacher's to run and it runs whether or not the page describes it; printed, it buries the one instruction that matters under a paragraph about a sequence the student cannot act on yet. The page states the job in front of them - "Do one task below" - and adds, in one short clause, only what stops them committing too hard too early: **"You may have to listen to it again," "You will read it again later."** Not when, not how many times, not what to do differently on the second pass. The student finds that out when the teacher gets there. |
| Differentiated participation / Foundation Support | Handled through the star system and task choice, never labeled or called out as a separate tier anywhere a student can see it. |
| Section numbers, prompt names, version narrative | Never appear. |
| Object logistics and object handling ("put it on your desk," "borrow one if you have none," "hold it up," "take out your...," "look at it," "point to the part") | Not printed; the object is a subject, not a prop (Quality Standards §D8). The packet prints the choice list and the task, nothing about where the object is or about looking at or pointing to it; a partner check asks the student to say which part a word describes. |
| Word-count targets (the 0.2 ranges in words; "count your words") | Students see a sentence count only ("3-6 sentences"), never a word range and never an instruction to count words; word targets stay in the Markdown for the teacher. |
| Pacing notes ("It is fine to finish tomorrow," "you have 20 minutes," "finish this first," "if there is time") and wrap-up lines ("Keep your piece," "You'll keep working on it soon") | Not printed; time is managed in class. The one continuation line allowed is the Pair position 4 hand-off note itself, never a closing line elsewhere. |
| A previous lesson's notes, planning, examples, or board ("last time," "your planning notes," "the example from earlier this week") | Never referenced; whatever this day's tasks need is reprinted or rebuilt in this packet (Quality Standards §D9). Only the piece a Set carries forward may be "the piece you wrote last time." |
| `**Answer note:**` lines and any other exemplar or expected answer in the Markdown | Not printed. Only the item's stem is carried into the packet, and the stem itself keeps no parenthetical that states what the item asks for (Quality Standards §C9). |

If a source lesson uses a term not listed here or in the modality's own rows, apply the same principle:
state the plain action the student takes, never the pedagogical name for it.

## F. Star ratings and lettered Tasks

**Stars.** Where the source lesson assigns different task Levels, represent difficulty with a star
rating: the lowest task Level in the band gets ★, and each step up the band's Task Levels row adds one
star, to ★★★★ for the highest (`Program_Conventions.md` §B has the per-band mapping). Show only filled
stars, never a filled-vs-empty display out of a fixed total. Do not label the tiers and do not frame the
set as a game ("choose your own adventure," "pick your challenge," "level up"); state only the section
heading and let the star count speak for itself.

**Routing: the page invites a plain choice, and never narrates who assigned what.** The lead-in is
"Choose one task." Two forms are wrong for the same reason, that both put a decision about the student on
the page instead of an instruction to them: routing by what the teacher does ("answer the Task your
teacher points you to," "do the Task your teacher gives you," "your teacher will tell you which one"),
and routing by an assigned star count ("do the Task with your number of stars"), which presumes the
student has been given a number and labels them with it. The star count is still how a student tells the
Tasks apart, and it still appears in the share instruction, where it does real work by pairing students
across different Tasks: "Choose one task. When you finish, find someone who did a task with a different
number of stars and tell them what you found." Where some Tasks are for everyone and the rest are
star-rated, say so plainly, once, in the lead-in that introduces the set: "Everyone does Tasks A and B.
Then choose one of the others." That sentence is not then repeated on the Tasks themselves. A Task printed
with no star tag is already an everyone-Task - the absence of stars is what says so - and appending
"Everyone does this one." to its instruction spends a line restating the page's own notation, which is the
first thing a student skips. The teacher
still steers individual students in the room; that steering is simply not printed.  Where two star levels' work differs in kind (a blank frame versus a blank writing
space), present each star's actual instruction as written; do not paper over the difference with
identical wording.

**Share instruction first.** Before a star-rated task set begins, the instruction to share with a
different-star group once finished sits BEFORE the task list, not after, so a student who reads only
their own task does not miss it. No framing language like "everyone teaches everyone something."

**One star rating per lettered Task; letters advance and never repeat.** Label exercises "Task A,"
"Task B," ... (never "Exercise" or "Activity"). A lettered Task carries exactly one star tag. Where the
source puts two task Levels under one shared activity, split it into two consecutive letters (lower star
first), repeating the instruction text and splitting any tier-specific clause along with it. Several
single-star blocks in a row each get their own advancing letter; never reuse "Task A" for each tier.
Reletter subsequent Tasks so the sequence stays continuous. Do not reorder a day's pedagogical sequence
to force one global ascending run; only the letters change. Task lettering restarts at A in each masthead
section. A self-check list ("Check Your Own Work") is a lettered Task like any other: one Task per star
level that has a list, each carrying exactly one star tag and repeating the items the levels share; never a
star tag on an individual list item, never two star tags on one line, and never one list with "three
stars: ..." notes inside it. An instruction shared by every level (the cross-out rule, "mark it as each
line says") sits as a plain line under the section title, before the Tasks. Sentence-stem lists keep
their one-star-per-stem form (below).

**No conditional extra work.** A packet never prints "Finished early?", "If you have time," "If you
finish," or any add-on gated on speed. A heavier tier is its own lettered, starred Task in the sequence or
is left out; the teacher decides live who moves on.

**Check-then-improve is one Task.** When a unit has a self-check and the revision that acts on it, they form
one section, "Check and Improve Your Writing," holding one lettered Task per star level: that level's check
questions first, then its improvement steps and answer space, in the same numbered list. Never a check
section followed by a revision section that repeats the same star sequence; like-star Tasks whose second half
acts on the first are merged. The wording is "improve," "make it better," "change," "make each change you
marked": never "fix" or "correct," since the piece is being improved, not repaired.

**Writing on printed text.** An instruction to write a correction above, between, or next to text the
packet itself printed only appears where the page has the room to write it. A line the student writes
into carries `.editable` on its list or block, opening the leading enough for a handwritten word to sit
above a printed one; crossing a word out, circling, or underlining needs no such room and is unaffected.
A printed block of more than about two lines is never annotated between its lines: at body leading there
is nowhere to put the words, and at `.editable` leading a paragraph runs off the page. Such a block is
marked up in place (cross out what is wrong) and then **rewritten in full on answer lines below**, which
also makes the corrected text, rather than a list of loose words, the thing the student produces. None of
this governs a student's own handwriting: "cross out the old version and write the new one above it" on
their own draft is theirs to space, and stays.

**A question is printed as a question.** Where an item simply asks something, the page asks it - "Why did
this day matter to him?" - not "In one sentence, say why this day mattered to him." The wrapper adds a verb
the student does not need and a length the answer line already states, and it turns the one thing that should
be scannable, the question, into the tail of an instruction. A stated length survives only where the length is
part of what the answer must do: "Summarize the repair in four sentences, in order" keeps its four sentences,
because four is the shape of the task. Clauses that carry a real constraint stay too, after the question mark:
"Why did this matter to him? Use what he says, not what you assume."

**Instructions as steps, and when not to use them.** Numbered steps are for actions a student could stop
between: each one has its own product, its own target, or a choice to make (a self-check list, a Task with a
written answer per part). A Task like that is a one-sentence lead line after the label and star ("Check your
paragraph, then make it better.") followed by a numbered list, one action or one question per step, in the
order the student does them; a check item is a question ("Is there one clear reason with because, since, as,
or given that?"), not a statement. A blank or answer line sits inside the step that needs it.

**Counting answer lines.** Answer space is counted from the expected answer, at roughly **eight to ten
handwritten words per full-width `.ans-line`** - student handwriting is far larger than the 14.5px body type,
so lines are never counted off how many printed lines the same text occupies. Three cases follow from it, and
each is counted rather than eyeballed:

- **Copied or rewritten text** (an editing paragraph written out corrected, a sentence recopied): count the
  words of the text itself and divide. An 82-word paragraph takes 9 lines, not the 5 it prints in.
- **A sentence the student composes** at the frame and paragraph Levels: two lines, not one. They write large,
  they cross out and try again, and a sentence that runs a few words long has nowhere to go.
- **A prompt that asks for exactly one line** ("Write one line saying what it withholds") keeps one line.
  That is the answer's stated length, not an under-sized space.

**An organizer cell is counted the same way, and its rows follow the input.** A `.notes-table` cell is a
response space, so its height is counted from what that row is expected to hold, never left at the default
because the default is what the class ships with. Two cases:

- **A cell holding a phrase** - one link of a chain, one column of a K-W-L - keeps the base
  `.notes-table td` height.
- **A cell holding everything a student took from one delivered part of the input** - a played segment, a
  chapter, a scene - takes `.notes-tall` on the table (§H.1), which is sized for three or four handwritten
  lines. A row standing in for five minutes of listening and a row standing in for one phrase are not the
  same size, and printing them the same tells the student to write one phrase.

**Where the source has a named part structure, the organizer's rows are that structure.** One row per part,
in the source's own order, each row naming its part and saying where that part sits in the source: a
timestamp range for a clip ("Part 3 · 5:27-10:18"), the section or chapter heading for a text. This holds
whether or not the delivery pauses. Where the input is **delivered in named parts** (Quality Standards
§D15), the locator tells the student which box the pause is for, and an organizer whose rows cut across the
parts leaves them nowhere to write during the pause the segmenting exists to give them. Where a short input
**plays or is read straight through**, the same locator is a signpost: a student who has lost the thread can
see which stretch is running and rejoin at the right row instead of guessing. Say which it is - a locator on
a straight-through source is a place-finder, not a cue to stop.

Rows labelled with bare counters - "Step 1, Step 2, Step 3" - carry none of that. They tell a student how
many boxes there are and nothing about which one they are in, which is the one thing a student who has
fallen behind needs. Use them only where the source genuinely has no part structure to name. Number the rows
from 1 on the student page in the source's own order; the lesson's teacher-side segment label stays off it
(§E).

Over-provisioning is its own fault: a dozen lines under a task that needs nine pushes what follows onto another
page and tells the student the answer should be longer than it is.

**One continuous procedure is one instruction, not a numbered list.** Where the parts run together on one
object in a single pass and only the last leaves anything on the page - read this, mark what is wrong, write
it out corrected - they are written as one instruction of two or three clauses, with the answer lines under
it. Numbering them adds a lead sentence that says what the steps are about to say, then splits one motion
into parts no student performs separately, and it reads on the page as being asked three questions. Two or
three clauses in one sentence is not the prose paragraph of chained instructions this guide forbids; that
means a block of prose burying several separable tasks with no numbering and no answer space of their own.

**Ascending order within a Task.** Where a Task contains more than one star-rated block, blocks appear
in ascending star order regardless of the source's order.

**Task label line.** The label sits inline with its instruction ("Task A. Answer using the text...") or,
where the instruction would crowd the star, alone on its own line followed by the instruction. Never a
bordered badge, and never a generic placeholder like "Complete the activity for your level."

**No star tag inside a teaching callout, title or body.** A grammar box, strategy box, worked model, or
any whole-class teaching content is delivered to the whole room; a star anywhere in it misrepresents
part of it as skippable. State any Level-varying content as plain sentences inside the callout; stars
belong only on the practice tasks that follow. Every teaching callout appears before every task that
depends on the concept it teaches; if the source lesson's own order would place it after, flag the
source (its Quality Standards §D5 sequencing rule), do not silently reorder.

**Sentence stems.** List star-coded stems one per star level, the stem alone. No coaching note under a
stem ("practice it quietly with a partner first," a tally task to do while waiting, advice on when to
use the line) - delivery is teacher-led facilitation, not page content.

**Every standalone question gets a number.** Any prompt with a referenceable response (a written answer,
a guess, a prediction), inside or outside a star-rated task, is numbered with the same `.num`/`.qbody`
pattern; a lone prompt outside a `<ol class="qlist">` uses `.qitem`. Multiple response lines under one
prompt are one question. Fillable organizers are referenced by name, not numbered; options inside one
question are not numbered.

**Placement.** A word bank, sentence frame, starter box, or model sits immediately before the item(s) it
serves, inside that item's block if it serves only one, never after the last item that needs it.

**Word banks.** One markup form in every modality. A bank is a `.wordbank` div containing plain inline
text: a single-list bank is one line, `<strong>Word bank:</strong>` then the items separated by
` &middot; `; a bank with categories is one `<strong>Category:</strong>` line per category, items
separated by ` &middot; `, lines joined by `<br />`. Nothing inside the div is wrapped in `<p>`,
`.model-step`, or any other class, and items are never comma-separated. A bank serving one task sits
inside that task block with no heading; a bank serving several tasks or a whole unit sits under a
`.section-title` reading exactly "Word Bank" (not "Your Word Bank," not a topic name), directly before
the first task that uses it, with any instruction about the bank after the div, not before it.
Fixed-frame items state their full instruction inline; a standalone frame box is reserved for a task with
a genuine speak-it-aloud step, and it renders before any instruction that refers back to it.

**A fixed frame is printed once per masthead section as a model** (in the grammar box, the word bank, or the
first Task that uses it: "It is ___ and ___."). Every later Task prints only the blank frame line the student
completes, and its lead says "Complete the frame" or "Write your sentence," never re-quoting the frame. The
packet's frame-regime Tasks also follow Quality Standards §D10: a section that shows the same
complete-the-frame Task twice for one star is a source-document error to report, not a layout to reproduce.

**Multiple choice.** Options fold into the question as an inline parenthetical list, one instruction line
at the top of the task block, no repeated verb per item and no option-per-line layout. A "circle one"
lead appears only above such a printed list; an item whose two choices sit only in the stem's wording
either prints them as the inline list or reads "Say which, and why" over its answer lines, never "Circle
one" (Quality Standards §C10). This is the one
stem parenthetical that may carry source content; every other parenthetical in a stem is limited by
Quality Standards §C9 (format, a choice menu with no correct option, or an untested gloss), and a
two-source compare layout prints each source's own content, never its tone or the contrast asked for, and
prints enough of it to compare from: at least three short verbatim excerpts per source on the same two or more
subjects (Quality Standards §C9), and only where that source cannot be re-inspected; where both sources are
printed in full on the student's page the layout carries no excerpts at all, just a labelled blank per source
for the student to fill (§C9). Two layouts are allowed for the excerpt case, chosen per lesson, both built on
the base `.match-list`/`.match-row` classes (§B): one `.match-row` per source with
its excerpts under the source label, or, when both sources speak to the same subjects, one `.match-row` per
subject with the subject as the `.match-label` and each source's excerpt on its own `.match-src` line opening
with the source's short name in bold. A genuinely
picture-based item embeds its real images (`.pic-options`, an `<img>` inside each `.pic-box`, the caption in
`.pic-label`); a packet never ships an empty picture box or a "[TEACHER: insert ...]" note. If no image can be
embedded, the item is rewritten around the student's own object or one in the room (Quality Standards §D8).

**Every printed text names its source.** The anchor text, a second comparison text, and any other block of
printed source material each carry a `.byline` under their headline saying where the text comes from ("From the
notebook of a walker who finished the trail in June," "From the trail association's route notes"). `.byline` is
not scoped to `.article` for exactly this reason: a second text sits in a `.refresher` block (each modality's own
packet prompt says where), and a student who has to infer which block is "the route notes" is being given a
puzzle the item never meant to set. Teacher-facing provenance stays out of it: never "Invented for this lesson."

**A packet never names an artifact it does not print or locate.** Student-facing text may refer to a chart,
organizer, list, model, or diagram only if the packet prints it or says where it is and gives the student their
own way into it - "Add one row to the class chart on the board. Write the row here first," over the student's own
answer line. A task that says "write it in the left column of your group's chart" when no chart is on the page
sends the student looking for something that does not exist, and a teacher-facing artifact named without its
location reads as a missing handout. A shared organizer built live on the board is a legitimate thing for a
lesson to have; it is not a legitimate thing for a task instruction to assume the student is holding. The same
applies to collaborative framing: a packet describes what one student does and then how they share it, never
assigns the student a group deliverable the page cannot hold.

**Embedded photos.** A hook photo or a task's picture prompt is one `<img class="photo" src="data:image/jpeg;base64,..."
alt="...">` immediately followed by its `.image-caption`. The source file lives in the lesson folder under its
Program Conventions §H name (`Lesson<N>_<Slug>_Img_<Purpose>.<ext>`) and the lesson `.md` names it at the point of
use; the packet embeds a downscaled copy (at most about 800px on the long side, roughly 100 KB), leaving the
source file unchanged. The caption is descriptive only ("The bird mural."); it never carries an author,
license, or "Wikimedia Commons" credit. Credits live in the Set's `Set<N>_<Band>_Image_Credits.md` (Program
Conventions §D, §I), built from the `.md`'s citation. A `.pic-options` grid gets no `.image-caption` at all -
its `.pic-label`s are the captions. `.image-placeholder` is only ever a box the student draws in, never a box
waiting for a photo.

## G. The Markdown document is the source of truth; the packet is always a regeneration

Run the packet prompt immediately after the lesson, homework, or assessment Markdown is complete, in
the same session, so the pair is produced together. The Markdown is the single source of truth. If a
review round asks for a change that affects what students actually read as a task, instruction, or
vocabulary item, do not patch the HTML directly: apply the change to the source Markdown first, then
re-run the packet prompt against it. Hand-editing the HTML for a content change leaves the Markdown
silently out of sync with what is actually taught, and the two drift further on every later
regeneration.

The only edits applied directly to the HTML without touching the Markdown are pure formatting or
translation-layer fixes that change no lesson content: a styling issue, a missed §E translation,
spacing or layout. The test: would a teacher reading the Markdown need to know this changed? If yes,
edit the Markdown and regenerate; if no, fix the HTML directly. A hand edit that adds markup first
confirms every class it uses is defined in that packet's `<style>`; a packet generated before a §B rule
existed gets its `<style>` synced to the current §B in the same edit, not left to render unstyled.

Deliver the HTML for visual review before treating it as final; apply feedback as scoped edits rather
than a full regeneration per round. Where a source lesson has a structural element no rule covers, apply
§E's principle (plain instruction over jargon) and this file's defaults (no color, no unnecessary rules,
callouts reserved for genuine spotlights, answer space matched to expected length), and reuse an existing
base class before adding a new one.

## H. Modality delta classes

Classes a modality's document structure needs that §B does not provide (§D). Each modality's block is
added to a packet only when generating that modality's packet.

### H.1 Listening/Speaking

`.citebox` (What You'll Watch citation), `.notes-table` (Listening Notes organizer), `.upside-down`
(closing script printed inverted), `.stop-flag`/`.stop-badge` (the Listening close's "Don't read ahead"
instruction in a heavy-bordered callout with a black octagonal STOP badge at its left; the badge is a drawn
shape with white text, never an emoji or image, so it prints identically everywhere), `.task-instr` (single top-of-task instruction line), `.qitem` (standalone numbered question), `.mc-list`/`.mc-letter`
(lettered answer choices), `.time-list` (response-time windows), `.verify-window`/`.verify-src`/`.verify-instr`
(the bounded verification window: a short stretch of the source's own words, printed after the response
spaces of every task it could answer, with its source label and timestamp range and the instruction to
cover it for the re-encounter; Quality Standards §D12), `.reader-copy`/`.reader-warn`
(teacher-only page in a separate file).

```css
.citebox {
  border: 1px solid var(--ink);
  padding: 12px 16px;
  margin: 10px 0 16px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.citebox strong {
  font-weight: 700;
}

.notes-table {
  width: 100%;
  border-collapse: collapse;
  margin: 10px 0 20px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.notes-table th,
.notes-table td {
  border: 1px solid var(--rule);
  padding: 8px 10px;
  text-align: left;
  vertical-align: top;
}
.notes-table th {
  font-weight: 700;
  background: #f2f2f2;
}
.notes-table td {
  height: 38px;
}
/* One row per delivered part (Quality Standards D15): sized for three or four
   handwritten lines, not a phrase. Applied to the table, not the cell. */
.notes-table.notes-tall td {
  height: 104px;
}

.upside-down {
  transform: rotate(180deg);
}

.stop-flag {
  display: flex;
  align-items: center;
  gap: 14px;
  border: 2px solid var(--ink);
  padding: 10px 14px;
  margin: 12px 0 14px;
  page-break-inside: avoid;
  break-inside: avoid;
}
.stop-badge {
  flex: 0 0 auto;
  width: 54px;
  height: 54px;
  background: var(--ink);
  color: var(--paper);
  clip-path: polygon(30% 0, 70% 0, 100% 30%, 100% 70%, 70% 100%, 30% 100%, 0 70%, 0 30%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: system-ui, -apple-system, sans-serif;
  font-weight: 700;
  font-size: 12px;
  letter-spacing: 0.04em;
  -webkit-print-color-adjust: exact;
  print-color-adjust: exact;
}
.stop-flag .instr {
  margin: 0;
}

.task-instr {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  font-style: italic;
  color: var(--ink-soft);
  margin: 0 0 10px;
}

.qitem {
  display: flex;
  gap: 10px;
  margin-bottom: 9px;
  font-size: 14.5px;
}

.mc-list {
  margin: 8px 0 4px 30px;
  padding-left: 0;
  list-style: none;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
}
.mc-list li {
  margin-bottom: 6px;
}
.mc-letter {
  font-weight: 700;
  margin-right: 6px;
}

.time-list {
  margin: 8px 0 4px;
  padding-left: 0;
  list-style: none;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
}
.time-list li {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid var(--rule-light);
  padding: 7px 2px;
}
.time-list li:last-child {
  border-bottom: none;
}
.time-list .time-window {
  color: var(--ink-soft);
  white-space: nowrap;
}

.reader-copy {
  border: 2px dashed var(--ink);
  padding: 14px 16px;
  margin: 20px 0;
  page-break-before: always;
}
.reader-copy .reader-warn {
  font-weight: 700;
  text-transform: uppercase;
  font-size: 12px;
  letter-spacing: 0.02em;
  margin-bottom: 10px;
}

.verify-window {
  border: 1px solid var(--ink);
  border-left: 4px solid var(--ink);
  background: var(--paper);
  padding: 12px 16px;
  margin: 18px 0 12px;
  page-break-inside: avoid;
}
.verify-window .verify-src {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.02em;
  color: var(--ink-soft);
  margin: 0 0 8px;
}
.verify-window p {
  margin: 0 0 8px 14px;
  font-size: 14px;
  line-height: 1.6;
}
.verify-window p:last-child {
  margin-bottom: 0;
}
.verify-instr {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
  font-style: italic;
  margin: 0 0 14px;
}
```

### H.2 Passage Reading

None. The base stylesheet is the whole of what a Passage Reading packet needs, including the
`.match-list`/`.match-row` compare layout and the `.pic-options`/`.pic-option`/`.pic-box`/`.pic-label`
picture-choice grid (both §B), each of which moved out of §H.1 once a second modality needed it.

### H.3 Academic Writing

`.rule-table` (grammar-rule and comparison tables; same visual pattern as `.notes-table`),
`.fillblank` (a fill-in-the-blank list whose items carry mid-sentence `.blank` spans), `.model-step`
(one worked line inside a Grammar or essay-structure callout). Add `.rule-table` to the packet's
`@media print` page-break-avoid list.

```css
.rule-table {
  width: 100%;
  border-collapse: collapse;
  margin: 10px 0 20px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.rule-table th,
.rule-table td {
  border: 1px solid var(--rule);
  padding: 8px 10px;
  text-align: left;
  vertical-align: top;
}
.rule-table th {
  font-weight: 700;
  background: #f2f2f2;
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
  letter-spacing: 0.03em;
}
```

### H.4 Assessment packets (all modalities)

`.checklist`: a plain self-check list (no borders, no table shape) with a checkbox glyph before each item, used
on a Speaking Task or Writing Task card to render the rubric's Meets column as student-facing checks.

```css
.checklist {
  margin: 10px 0 4px;
  padding-left: 0;
  list-style: none;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.checklist li {
  display: flex;
  gap: 8px;
  margin-bottom: 6px;
}
.checklist li::before {
  content: "\2610";
  flex-shrink: 0;
}
```

An assessment packet also gives each task Level's section `page-break-before: always` (except the first) so one
Level's pages print cleanly on their own, and carries no `.masthead-meta` stack, since one assessment spans every
Level in a band and has no single lesson version code.

## I. Shared packet self-check

Run this list first, then the modality's own list.

1. No §E left-column term, section number, or version narrative anywhere in student-facing text?
2. One combined document covering every task Level in the band, not per-Level handouts?
3. Objective stated as one "I can ..." sentence in the student's voice near the top of each masthead
   section, before any task content, naming the skill (not the object) with no "You will," "To," bare verb,
   "some of you," or other tier narration, and the closing activity connecting back to it? (§E; Quality
   Standards §D1)
4. Sessions labeled Unit _A / Unit _B (never "Day 1"/"Day 2"), folded into the heading text, task
   lettering restarting in each?
5. Every masthead, opening and later, carries the same two-line `.masthead-meta` stack (modality
   label, a `.masthead-sep` dot, then the Module name, never its number; Band plus
   `<Module>.<Set>.<Lesson>.<Version>` as one string), no Name/Date field, kicker, subtitle, or
   footer?
6. Stars: only filled stars, no Level number, tier name, or game framing; the routing lead-in a plain
   "Choose one task," never routing by what the teacher does ("the Task your teacher points you to") nor by
   an assigned star count ("the Task with your number of stars"); share instruction before the task list,
   with the star count used there to pair students across different Tasks; one star per lettered Task, self-check lists included, with no
   star on a list item or two stars on a line; letters continuous; ascending order within a Task; no star
   inside any teaching callout; no "Finished early?" or other speed-gated add-on; check and improve merged
   into one Task per star under "Check and Improve Your Writing," never two like-star sequences and never
   "fix"; every multi-step Task a one-sentence lead plus numbered steps, check items as questions? (§F)
7. Every teaching callout before the tasks that depend on it? (§F)
8. Every standalone question numbered; every bank, frame, starter, or model placed before the items it
   serves; multiple choice inline with one top instruction line, no "circle" instruction without a printed
   list; picture items with embedded images and no
   empty placeholder or "[TEACHER: insert ...]" note anywhere? (§F)
9. Stems listed alone, no coaching notes? (§F)
10. Callout boxes reserved for genuine spotlights; word banks using only the light dashed-rule exception
    and the one §F markup form (bold label, `&middot;` separators, `<br />` between category lines, a
    "Word Bank" section title only when the bank serves more than one task); no other ordinary content
    bordered?
11. Answer space counted from the expected answer at eight to ten handwritten words per full-width line, with
    copied text counted from its own word count, a student-composed sentence given two lines, and a stated
    one-line answer given one (`.blank` inside a sentence; `.ans-line-sm`/`.ans-line`
    standalone below a prompt, never mid-sentence), none where no written response is needed?
12. Every decorative, non-load-bearing horizontal rule removed?
13. Black-and-white only; no em-dashes; single self-contained HTML file with no external dependencies
    besides the print trigger; base stylesheet reused unmodified plus only that modality's §H classes;
    no selector in the packet's `<style>` that §B/§H doesn't define, and no body-text class at a size
    other than 14.5px (§D); §C markup conventions followed?
14. Produced by regenerating from the current Markdown, not by hand-editing a previous HTML for a
    content change? (§G)
15. No reference to an earlier lesson's notes, planning, examples, or board, other than the carried piece;
    at Beginner and Intermediate no reflection question, only actions with a visible product? (§E; Quality
    Standards §D9, §E6)
16. No object logistics or handling ("look at it," "point to," "hold it up"), no word range or "count your
    words," no pacing line, and no wrap-up or "keep working on it" line outside the Pair position 4 hand-off
    anywhere in student-facing text? (§E)
17. Each fixed frame printed once per masthead section as a model, later Tasks showing only the blank line,
    no lead re-quoting it, and no star given the same complete-the-frame Task twice in one section? (§F;
    Quality Standards §D10)
18. Every embedded image a base64 data-URI `<img class="photo">` (or a `.pic-box` `<img>`) with its rule
    present in `<style>`, a descriptive caption with no credit text (and none under a `.pic-options` grid), a
    §H-named asset file in the lesson folder that the `.md` names and cites, a row in the Set's
    `Image_Credits.md`, and no placeholder or teacher note anywhere? (§A.1, §F; Quality Standards §D8;
    Conventions §D, §I)
19. No `Answer note:` line or other exemplar answer printed, and no stem parenthetical or compare-layout
    text that states what its item asks the student to find? Where a source cannot be re-inspected (a clip, a
    second source not printed), every two-source compare layout holds at least three verbatim excerpts per
    source on shared subjects, in one of the two §F layouts. Where both sources are printed in full on the
    page, the layout prints **no** excerpts and no subject labels: it gives ruled space for the student to
    write each side's wording into, since finding and pairing them is the task. (§E, §F; Quality Standards §C9)
20. In a Listening/Speaking packet, the "Don't read ahead" instruction printed inside a `.stop-flag` callout
    with its `.stop-badge`, ahead of the response space, and the badge used nowhere else on the page? (§H.1)
21. No instruction to form a circle, move to a corner or station, walk the room, or rearrange seating; every
    discussion instruction runs from where the student sits, and a rotation prints as finding a new
    partner? (§E, Quality Standards §D11)
22. No item answered by reading a chromatic color off a printed picture: no picture task turning on one, no
    chromatic color offered as an answer option or word-bank entry about a photograph, and no expected answer
    naming one (A.2). Picture items use size, shape, quantity, texture, pattern, setting, or black/white/gray,
    all of which survive grayscale. Color is still fine where the student describes their own belonging.
23. In a packet carrying a verification window, does the window sit after the response spaces of every task
    it could answer, carry its source label and timestamp range, stay inside the lesson's stated ceiling, hold
    no task, answer or `Answer note:` inside it, and close with the instruction to cover it for one more
    unsupported encounter? (Quality Standards §D12, §H.1)
24. Does the opening section state the lesson's topic and what kind of text, clip, or scenario is coming before
    its first question, and is every question there answerable from that orientation, from something printed on
    the page, from the student's own life, or as an opinion? No "you do not know yet what this is," no asking who
    is speaking in an unattributed quote or what an uncaptioned picture shows, and no answer line under a question
    the page has made unanswerable. (Quality Standards §D13)
25. Is every footnote reference a `<span class="footref">` holding a plain ASCII digit, with no `<sup>` wrapper
    and no Unicode superscript character, and does the packet's `<style>` carry §B's current `.footref` rule so
    the numeral actually prints raised rather than as a bold digit run into the word? (§B, §C)
26. Every student-facing list of paired items (base form to past form, word to meaning, term to
    example) rendered as a `.rule-table`/`.notes-table` with a header row naming both columns, laid
    two across where the pairs are short, and never as a comma-run of pairs inside a `<p>` or
    `.model-step`? (§C)
27. Every instruction to write above, between, or next to packet-printed text backed by the room to do it:
    `.editable` leading on the line or block written into, and no multi-line printed block annotated between
    its lines rather than crossed out and rewritten in full on answer lines below? (§F)
28. Numbered steps used only where a student could stop between them (each with its own product, target, or
    choice), with any single continuous procedure on one object written as one instruction of two or three
    clauses over its answer lines instead? (§F)
29. Does every chart, organizer, list, model, or diagram named in student-facing text either appear on the page
    or carry its location plus the student's own line into it, and does no instruction hand the student a group
    deliverable the packet cannot hold? (§F)
30. Is "everyone does this" stated once in the set's lead-in and nowhere else, with no un-starred Task
    carrying a sentence restating that it is for everyone? (§F)
31. Is every organizer cell's height counted from what the row holds rather than left at the default - and
    where the source has a named part structure, does the organizer carry one row per part, in the source's
    own order, each naming its part and its locator into the source (a timestamp range, a section heading),
    on a `.notes-tall` table - whether the delivery pauses between parts or runs straight through, and never
    bare "Step 1, Step 2" counters where a real part structure exists? (§F, §H.1)
32. Is the page free of delivery mechanics - who presses play, when it stops, how long a beat lasts - with
    anything the task genuinely turns on stated as what the student will hear rather than as what the teacher
    will do? (§E)
33. Is every item that simply asks something printed as the question itself, with no "In one sentence, say
    why ..." wrapper, and a stated length kept only where the length is part of what the answer must do? (§F)
34. Is the lesson's staging kept off the page - no commit-then-replay-then-revise script, no "before anything
    is played again," no account of what a later pass will ask - with the instruction stating the job in front
    of the student plus at most one short clause telling them the input comes back ("You may have to listen to
    it again")? (§E)
35. Does no name for the skill itself reach the printed page unless the page teaches it - "time connectors,"
    "sequence markers," "transition words," "topic sentence" - checked by searching the finished packet for
    the term rather than by reading, since the standard failure is one unglossed instance in the highest
    tier's stem while every other mention was paraphrased? (§E)

## Changelog

**Current version: v2.48.** For the full dated version history and the reasoning behind each
change, see `Changelog.md`.
