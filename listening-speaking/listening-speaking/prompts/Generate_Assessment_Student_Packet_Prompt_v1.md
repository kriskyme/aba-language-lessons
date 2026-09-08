# Listening/Speaking Assessment Student Print Formatting Prompt (v1)

Companion to the Assessment Generation Prompt (v1). Takes one completed Set assessment (Part A
Listening, Part B Speaking) and produces a single, print-ready, black-and-white student handout:
one self-contained HTML document, with every piece of teacher-facing language, and everything a
student should never see (Part A's answer keys, point values, holistic pass notes; Part B's actual
rubric and any submission-mechanism info), removed or translated. **The one exception:** a short
self-check checklist derived from Part B's rubric Meets column appears on each Speaking Task card
(Section 0) - not the rubric itself. Mirrors the Student Print Formatting Prompt (v1) closely - same
translation principle, same base stylesheet, same star-rating system for labeling task Levels on a
page - adapted for an assessment's shape rather than a taught lesson's.

Use this prompt only after an Assessment `.md` already exists in full (both Part A and Part B). Do
not use it to generate assessment content, invent new items, or omit a task Level present in the
band. This produces the **student version only**.

## SECTION 0: SCOPE AND INPUTS

Required: the completed Assessment `.md`, supplied in full - Part A's source citation(s) (one per
clip) and segment labels, all four task Levels' items (vocabulary is folded into each Level's own
item set, not a separate list), and Part B's per-Level speaking prompts. Pull all content directly
from the completed assessment; do not invent new vocabulary or items, and do not drop a task Level
present in the source band.

**Never carry these into the student copy, under any heading or phrasing:** any of Part A's answer
keys or bracketed `[Answer: ...]` tags, point values or item score weights, or holistic pass-note
language ("a passing performance looks like..."). None of this is student-facing content - it is
the reason this is a separate prompt from the assessment itself rather than a formatting pass over
the same document.

**The one exception: a checklist derived from Part B's rubric (B.4) Meets column** appears on that
Level's own Speaking Task card - one item per criterion, phrased as something the student can check
off before submitting, using that criterion's Meets-column language reworded directly to the
student where needed. The rubric's Not yet/Developing columns and its table shape are never shown -
this is a self-check checklist, not the teacher's scoring instrument (2.7). Do not carry over any
submission-mechanism information either (platform name, submit-by date, re-recording note, or
same-task live-delivery note) - all of that is teacher-communicated logistics, not part of this
document.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

None of the left column may appear in the student-facing document.

| Teacher-facing term | Student-facing translation |
| --- | --- |
| Listening/Speaking Strategy names ("Recognize Examples," etc.) | Not named as a strategy; the item itself just asks the question, the same way a lesson's tasks never narrate "today we are practicing X." |
| Task Level / Level (numeric) | A star rating (★ to ★★★★) used only to label which page a student was assigned, never a menu to choose from - an assessment is not student-choice the way a lesson's differentiated task block is. |
| `[Answer: ...]` tags, point values, holistic pass notes (Part A only) | Never shown. Removed entirely (Section 0). |
| Rubric (B.4), Not yet/Developing/Meets criteria | Never shown as a rubric or table. Translated into a plain self-check checklist (one item per criterion, Meets-column language reworded to the student) on that Level's own Speaking Task card (Section 0, 2.7). |
| "Emphasizes Making Comparisons / Sequencing Language" (B.3 framing) | Rephrased as a plain instruction folded into the task itself (e.g. "Compare the two rooms, then explain the order you'd show them"), never labeled as a skill being measured. |
| Teams Speaking Progress (internal mechanism name), submission date, re-record/live-delivery note | Not shown at all - no platform name, no submit-by date, no recording-mechanism note anywhere on the card. All of this is teacher-communicated logistics, outside this document (2.7). |
| Segment labels ([Segment N: ...]) | Shown in plain form, same treatment as the lesson packet - a real navigational aid for finding a spot in the recording during replay. |
| "New, unseen source" / "transfer check" framing | Not named as such; the student simply sees the citation box and the test, the same way a lesson never tells students they're being "assessed for transfer." |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document, two sections

Produce a single shared document, not per-task-Level handouts, in two sections mirroring the
source assessment's two parts: a **Listening Test** section (Part A) and a **Speaking Task**
section (Part B). Unlike the lesson packet's Unit A/Unit B (which represent two taught class
days), these two sections represent one in-class test period (Listening) and one take-home
recording task (Speaking) - label them plainly as what they are, not as "Unit" or by day.

### 2.2 Per-Level pages, not a differentiation menu

An assessment is not student-choice: the teacher assigns each student one task Level. Print each
task Level's Listening Test material as its own clearly labeled page or page-break section (e.g.
"Listening Test - ★★" as a running head), containing only that Level's own items, so a teacher can
distribute (or photocopy) selectively - the same selective-printing need the Assessment Generation
Prompt's own scope note anticipates. Do not merge all four Levels' items into one shared
choose-your-task block the way the lesson packet's star-rated tasks work; here, "choose" already
happened when the teacher assigned the Level.

### 2.3 What You'll Listen To

Include one short boxed citation per clip (the source assessment may use 2-3 clips, not just one) -
title, one clear sentence describing what it's about, and platform - same style and content
restrictions as the lesson packet's 2.3 (no runtime, no editor/adapter credits, no line inviting
students to ask their teacher for the link). Place all clips' citation boxes together at the top of
the Listening Test section, immediately before the first task Level's items - there is no notes
organizer to place them before (2.5). Where the assessment uses segment labels, carry the plain
segment name into any item that references a specific part of a recording.

### 2.4 No kicker lines, no metadata fields

Same as the lesson packet's 2.4: no Name/Date field, no module/band kicker, no subtitle line, no
footer note. (A teacher distributing a specific Level's page by hand does not need a printed Level
kicker either - the running head from 2.2 already shows it.)

### 2.4a Every question gets a number

Same rule as the lesson packet's 2.4a: any place a student produces a specific, referenceable
response gets a number via the shared `.num`/`.qbody` (`.qlist`) or standalone `.qitem` pattern.
Fillable organizers (the comparison T-chart) are referenced by name, not numbered.

### 2.5 No separate vocabulary list or notes organizer

Unlike the lesson packet, this assessment's student copy has no "Words to Know" list and no
notes-taking organizer - per the current Assessment Generation Prompt, vocabulary is tested only
through the numbered items themselves (word-to-definition matching or fill-in-the-blank, wherever
the source `.md` places it in a Level's item set), and there is no free-form notes phase to print a
table for. Do not add either back in; if the source `.md` is missing both (as it should be), that is
correct, not an omission to fix.

### 2.6 Listening Test items

Print that page's one assigned Level's items as plain numbered questions (the `.qlist` pattern),
in the same order as the source assessment. Every item is multiple choice, fill-in-the-blank, or
matching (the current Assessment Generation Prompt's item-format rule) - there is no open-ended
answer line to size. Apply the same compact-formatting rules as the lesson packet's 2.7:
multiple-choice options folded inline as a parenthetical list with one top-of-page instruction line
(not a repeated verb per item); genuinely picture-based items get real labeled placeholder boxes;
word banks sit immediately before the item(s) they serve; matching items use the `.match-list`/
`.match-row` pattern already established (one pair per line); a "predict, then confirm" item stays
a single numbered item with its prediction circle and its confirm circle presented as one instruction
("circle your prediction... then circle what the recording actually says"), not two separate
numbered steps, since both halves are the same objectively-scored item. Never print the item's
answer, point value, or which strategy it is testing.

### 2.7 Speaking Task cards

For each task Level, print an instruction card with these parts, in order: the topic in plain
language; the task's concrete, countable content requirements (B.3's per-Level requirements -
these are the actual instructions, not a restated verb); the target length; and a short self-check
checklist (`.checklist`, 3) titled "Before you submit, check:" - one item per that Level's rubric
(B.4) criterion, using its Meets-column language reworded directly to the student (e.g. "Both rooms
described using the fixed frame," not "Both rooms clearly described in two-slot frame" left in
third person). Do not print the rubric's Not yet/Developing columns or any table shape - this is a
self-check list, not the teacher's scoring instrument. Do not print any submission-mechanism
information anywhere on the card or elsewhere in the document - no platform name, no submit-by
date, no re-recording note, no same-task live-delivery note; all of that is teacher-communicated
logistics, not part of this document. Any "emphasizes X skill" framing from the source (B.2/B.3)
gets folded into the task's own wording (Section 1's translation row) rather than named as a
measured skill. Use the star system (2.2) to label which Level's card a student was given; do not
print all four Levels' cards as a choose-your-own menu on a single student's copy unless the
teacher is distributing a multi-Level reference sheet on purpose (flag this as a teacher decision,
not this prompt's default).

### 2.8 Callout boxes, answer space, redundant rules

Same rules as the lesson packet's 2.13: callouts reserved for genuine spotlights (the citation
box), word banks get the dashed-rule exception only, answer space matched to expected answer
length, no decorative rules.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Identical to the lesson packet's Section 3: single self-contained HTML file, black-and-white only,
no em-dashes, print-safe page breaks. **Reuse `shared/Student_Packet_Style_Guide.md`'s base
stylesheet directly, plus the CSS class additions already established in the Student Print
Formatting Prompt (v1)** (`.citebox`, `.task-instr`, `.pic-options`/`.pic-option`,
`.match-list`/`.match-row`, `.qitem`) rather than inventing new ones. `.notes-table`/`.vocab-list`
are retired along with the sections they served (2.5) - do not include their CSS in a newly
generated packet. **`.checklist` is this family's one new delta class** (2.7): a plain list (no
borders, no table shape) with a checkbox glyph (`&#9744;`) before each item, for printing a Speaking
Task's self-check checklist - deliberately plainer than a table, since this is a student self-check
list, not the teacher's scoring instrument. Add a page-break rule between each task Level's Listening Test page
(`page-break-before: always` on each Level's section) so selective printing (2.2) produces clean
single-Level printouts.

## SECTION 4: WORKFLOW

**Generation timing:** run this prompt immediately after an Assessment `.md` is complete, in the
same session/request - not as a separately-requested later step, the same same-session pairing
rule the Lesson Generation Prompt's third addendum established for lessons and their packets. An
assessment request produces both files together: the `.md` first, then this prompt run against
that finished `.md` to produce the `.html`.

**The `.md` is the single source of truth; this prompt's output is always a regeneration, never a
standalone edited artifact.** If a review round asks for a change that affects what students
actually see as an item, topic, or instruction, apply the change to the source Assessment `.md`
first, then re-run this prompt to produce a fresh `.html`. The only edits safe to apply directly to
the `.html` are pure formatting/translation-layer fixes that don't change assessment content.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

- Does every left-column term from Section 1 appear nowhere in student-facing text?
- Is every Part A answer key tag, point value, and holistic pass note absent from the document -
  not just hidden, actually removed (Part B's rubric is the one deliberate exception - see below)?
- Are the two sections labeled Listening Test and Speaking Task (not "Unit," not by day)?
- Does each task Level's Listening Test material appear on its own clearly labeled page, containing
  only that Level's own items - not a four-Level choose-your-task menu?
- Does a "What You'll Listen To" citation box appear for every clip the source assessment uses,
  together at the top of the Listening Test section, avoiding any line inviting students to ask
  their teacher for the link?
- Is there no vocabulary list and no notes-taking organizer anywhere in the document (2.5) - is
  vocabulary tested only inside the numbered items, the same as every other item?
- Does every standalone question carry a number via `.qitem` or `.qlist`?
- Do multiple-choice items stay on one compact line each, with genuinely picture-based items given
  real labeled placeholder boxes, matching items using `.match-list`/`.match-row`, and word banks
  placed immediately before the item(s) they serve?
- Does each Speaking Task card include the topic, concrete/countable content requirements (not just
  a restated target length), and target length, with any skill-emphasis framing folded into the
  task's own wording rather than named as a measured skill?
- Does each Speaking Task card show a `.checklist` self-check list (one item per rubric criterion,
  Meets-column language reworded to the student) rather than the rubric's Not yet/Developing
  columns or a table shape - and does no submission-mechanism information (platform name, submit-by
  date, re-record/live-delivery note) appear anywhere on the card or elsewhere in the document?
- Is the document black-and-white, em-dash-free, single self-contained HTML file, reusing the
  existing base stylesheet plus only the classes already documented for this family?
