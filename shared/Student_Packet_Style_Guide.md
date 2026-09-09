# Student Packet Style Guide (v2.14)

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
  margin-bottom: 6px;
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
  gap: 4px;
  margin-top: 4px;
}
.masthead-tag {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--ink);
  white-space: nowrap;
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

The document's opening masthead (only - never a later `.masthead.masthead-later` heading) includes
a `<div class="masthead-meta">` alongside the `h1`, holding exactly two stacked
`<span class="masthead-tag">` lines, in this order:

1. That modality's plain class label (`Reading`, `Listening & Speaking`, or `Writing` - see each
   lesson type's own Student Packet prompt §2.4 for which one).
2. The lesson's Band and its version code, combined as one space-separated string:
   `<Band> <Module>.<Set>.<Lesson>.<Version>` (e.g. `Advanced 1.1.1.0`). Band is plain language
   (`Beginner`, `Intermediate`, `Advanced`, or `Proficient`); the version code format is defined in
   `Program_Conventions.md` §G - the lesson number in it is the global one from
   `Program_Conventions.md` §C, not restarted per Set.

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
- **Quoted CSS values** (a font name with a space in it, `content: ""`) use double quotes, matching
  the double quotes already used for every HTML attribute.

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
| Fishbowl / Town Hall / Concentric Circles / Jigsaw / discussion carousel | A plain small-group discussion instruction: get into a group, here are your questions, take turns talking. Do not name the protocol. Render as simultaneous small groups (a static page cannot run a live rotation) and fold any outer-circle or tracking task into a group's own task rather than dropping it. |
| Activation hooks by name (K-W-L Walk, Mystery Quote, Stand Up/Move, Four Corners, etc.) | The plain instruction the activity produces (a warm-up question, a prompt to discuss), never the activity's name - in headings included. |
| Internal item labels (STOP & CHECK, Fact Finder, Cause & Effect set, controlled-practice type names) | Ordinary numbered or lettered questions with no internal label carried into student view. |
| Board-dependent moment | Not shown to students at all; teacher-only classroom-management instruction. |
| Differentiated participation / Foundation Support | Handled through the star system and task choice, never labeled or called out as a separate tier anywhere a student can see it. |
| Section numbers, prompt names, version narrative | Never appear. |
| Object logistics and object handling ("put it on your desk," "borrow one if you have none," "hold it up," "take out your...," "look at it," "point to the part") | Not printed; the object is a subject, not a prop (Quality Standards §D8). The packet prints the choice list and the task, nothing about where the object is or about looking at or pointing to it; a partner check asks the student to say which part a word describes. |
| Word-count targets (the 0.2 ranges in words; "count your words") | Students see a sentence count only ("3-6 sentences"), never a word range and never an instruction to count words; word targets stay in the Markdown for the teacher. |
| Pacing notes ("It is fine to finish tomorrow," "you have 20 minutes," "finish this first," "if there is time") and wrap-up lines ("Keep your piece," "You'll keep working on it soon") | Not printed; time is managed in class. The one continuation line allowed is the Pair position 4 hand-off note itself, never a closing line elsewhere. |
| A previous lesson's notes, planning, examples, or board ("last time," "your planning notes," "the example from earlier this week") | Never referenced; whatever this day's tasks need is reprinted or rebuilt in this packet (Quality Standards §D9). Only the piece a Set carries forward may be "the piece you wrote last time." |

If a source lesson uses a term not listed here or in the modality's own rows, apply the same principle:
state the plain action the student takes, never the pedagogical name for it.

## F. Star ratings and lettered Tasks

**Stars.** Where the source lesson assigns different task Levels, represent difficulty with a star
rating: the lowest task Level in the band gets ★, and each step up the band's Task Levels row adds one
star, to ★★★★ for the highest (`Program_Conventions.md` §B has the per-band mapping). Show only filled
stars, never a filled-vs-empty display out of a fixed total. Do not label the tiers and do not frame the
choice as "choose your own adventure" or "pick your challenge"; state only the section heading and let
the star count speak for itself. Which star a student works at is decided live by the teacher, not
narrated on the page. Where two star levels' work differs in kind (a blank frame versus a blank writing
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

**Instructions as steps.** A Task whose instruction has more than one action or question is a one-sentence
lead line after the label and star ("Check your paragraph, then make it better.") followed by a numbered
list, one action or one question per step, in the order the student does them; a check item is a question
("Is there one clear reason with because, since, as, or given that?"), not a statement. Never a prose
paragraph of chained instructions. A blank or answer line sits inside the step that needs it.

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
at the top of the task block, no repeated verb per item and no option-per-line layout. A genuinely
picture-based item embeds its real images (`.pic-options`, an `<img>` inside each `.pic-box`, the caption in
`.pic-label`); a packet never ships an empty picture box or a "[TEACHER: insert ...]" note. If no image can be
embedded, the item is rewritten around the student's own object or one in the room (Quality Standards §D8).

**Embedded photos.** A hook photo or a task's picture prompt is one `<img class="photo" src="data:image/jpeg;base64,..."
alt="...">` immediately followed by its `.image-caption`. The source file lives in the lesson folder under its
Program Conventions §H name (`Lesson<N>_<Slug>_Img_<Purpose>.<ext>`) and the lesson `.md` names it at the point of
use; the packet embeds a downscaled copy (at most about 800px on the long side, roughly 100 KB), leaving the
source file unchanged. `.image-placeholder` is only ever a box the student draws in, never a box waiting for a
photo.

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
(closing script printed inverted), `.task-instr` (single top-of-task instruction line), `.pic-options`/
`.pic-option` (picture items with embedded images), `.match-list`/`.match-row` (matching items, one pair per line,
label above a full-width `.ans-line`), `.qitem` (standalone numbered question), `.mc-list`/`.mc-letter`
(lettered answer choices), `.time-list` (response-time windows), `.reader-copy`/`.reader-warn`
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

.upside-down {
  transform: rotate(180deg);
}

.task-instr {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  font-style: italic;
  color: var(--ink-soft);
  margin: 0 0 10px;
}

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
  border: 2px dashed var(--ink);
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 10.5px;
  color: var(--ink-soft);
  padding: 6px;
}
.pic-option .pic-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12.5px;
  text-align: center;
  margin-top: 5px;
}

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
```

### H.2 Passage Reading

None. The base stylesheet is the whole of what a Passage Reading packet needs.

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
5. Opening masthead only carries the two-tag `.masthead-meta` stack (modality label; Band plus
   `<Module>.<Set>.<Lesson>.<Version>` as one string), no Name/Date field, kicker, subtitle, or footer?
6. Stars: only filled stars, no Level number, tier name, or "choose your adventure" framing; share
   instruction before the task list; one star per lettered Task, self-check lists included, with no
   star on a list item or two stars on a line; letters continuous; ascending order within a Task; no star
   inside any teaching callout; no "Finished early?" or other speed-gated add-on; check and improve merged
   into one Task per star under "Check and Improve Your Writing," never two like-star sequences and never
   "fix"; every multi-step Task a one-sentence lead plus numbered steps, check items as questions? (§F)
7. Every teaching callout before the tasks that depend on it? (§F)
8. Every standalone question numbered; every bank, frame, starter, or model placed before the items it
   serves; multiple choice inline with one top instruction line; picture items with embedded images and no
   empty placeholder or "[TEACHER: insert ...]" note anywhere? (§F)
9. Stems listed alone, no coaching notes? (§F)
10. Callout boxes reserved for genuine spotlights; word banks using only the light dashed-rule exception
    and the one §F markup form (bold label, `&middot;` separators, `<br />` between category lines, a
    "Word Bank" section title only when the bank serves more than one task); no other ordinary content
    bordered?
11. Answer space sized to the expected answer (`.blank` inside a sentence; `.ans-line-sm`/`.ans-line`
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
    present in `<style>`, a caption, a §H-named asset file in the lesson folder that the `.md` names, and no
    placeholder or teacher note anywhere? (§A.1, §F; Quality Standards §D8)

## Changelog

**Current version: v2.14.** For the full dated version history and the reasoning behind each
change, see `Changelog.md`.
