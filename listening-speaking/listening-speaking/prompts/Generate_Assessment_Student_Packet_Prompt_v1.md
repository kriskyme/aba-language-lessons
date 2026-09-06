# Listening/Speaking Assessment Student Print Formatting Prompt (v1)

Companion to the Assessment Generation Prompt (v1). Takes one completed Set assessment (Part A
Listening, Part B Speaking) and produces a single, print-ready, black-and-white student handout:
one self-contained HTML document, with every piece of teacher-facing language, and everything a
student should never see (answer keys, point values, holistic pass notes, rubrics), removed or
translated. Mirrors the Student Print Formatting Prompt (v1) closely - same translation principle,
same base stylesheet, same star-rating system for labeling task Levels on a page - adapted for an
assessment's shape rather than a taught lesson's.

Use this prompt only after an Assessment `.md` already exists in full (both Part A and Part B). Do
not use it to generate assessment content, invent new items, or omit a task Level present in the
band. This produces the **student version only**.

## SECTION 0: SCOPE AND INPUTS

Required: the completed Assessment `.md`, supplied in full - the Part A source citation and segment
labels, the vocabulary list, the Play & Notes organizer, all four task Levels' tiered items, and
Part B's per-Level speaking prompts. Pull all content directly from the completed assessment; do
not invent new vocabulary or items, and do not drop a task Level present in the source band.

**Never carry these into the student copy, under any heading or phrasing:** any answer key or
bracketed `[Answer: ...]` tag, any point value or item's score weight, any holistic pass-note
language ("a passing performance looks like..."), any rubric or its Not yet/Developing/Meets
criteria, and any teacher-only scoring instruction. None of this is student-facing content - it is
the reason this is a separate prompt from the assessment itself rather than a formatting pass over
the same document.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

None of the left column may appear in the student-facing document.

| Teacher-facing term | Student-facing translation |
| --- | --- |
| Listening/Speaking Strategy names ("Recognize Examples," etc.) | Not named as a strategy; the item itself just asks the question, the same way a lesson's tasks never narrate "today we are practicing X." |
| Task Level / Level (numeric) | A star rating (★ to ★★★★) used only to label which page a student was assigned, never a menu to choose from - an assessment is not student-choice the way a lesson's differentiated task block is. |
| `[Answer: ...]` tags, point values, holistic pass notes | Never shown. Removed entirely (Section 0). |
| Rubric (B.4), Not yet/Developing/Meets criteria | Never shown to the student on this document; a rubric is teacher-facing scoring material, not a task instruction. |
| "Emphasizes Making Comparisons / Sequencing Language" (B.3 framing) | Rephrased as a plain instruction folded into the task itself (e.g. "Compare the two rooms, then explain the order you'd show them"), never labeled as a skill being measured. |
| Teams Speaking Progress (internal mechanism name) | A plain instruction: how to record, where to submit, and by when. Keep the platform name (students do need to know which app to open) but drop any scoring-mechanism language. |
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

Include a short boxed citation - title, one clear sentence describing what it's about, and
platform - same style and content restrictions as the lesson packet's 2.3 (no runtime, no
editor/adapter credits, no line inviting students to ask their teacher for the link). Place it
immediately before the Play & Notes organizer, the same position rule as the lesson packet. Where
the assessment uses segment labels, carry the plain segment name into any item that references a
specific part of the recording.

### 2.4 No kicker lines, no metadata fields

Same as the lesson packet's 2.4: no Name/Date field, no module/band kicker, no subtitle line, no
footer note. (A teacher distributing a specific Level's page by hand does not need a printed Level
kicker either - the running head from 2.2 already shows it.)

### 2.4a Every question gets a number

Same rule as the lesson packet's 2.4a: any place a student produces a specific, referenceable
response gets a number via the shared `.num`/`.qbody` (`.qlist`) or standalone `.qitem` pattern.
Fillable organizers (the comparison T-chart) are referenced by name, not numbered.

### 2.5 Listening Notes organizer

Print the source assessment's Play & Notes organizer (typically a comparison T-chart for a
Describing-module assessment, matching the Set's own lessons) as a simple fillable table with the
assessment's own row labels, positioned before the numbered test items so students can fill it in
while the source plays. Match "watch"/"listen" wording to the source's real, confirmed media type,
same rule as the lesson packet's 2.6 - do not default to "watch."

### 2.6 Listening Test items

Print that page's one assigned Level's items as plain numbered questions (the `.qlist` pattern),
in the same order as the source assessment, with a real answer line matched to expected answer
length. Apply the same compact-formatting rules as the lesson packet's 2.7: multiple-choice options
folded inline as a parenthetical list with one top-of-page instruction line (not a repeated verb
per item); genuinely picture-based items get real labeled placeholder boxes; word banks sit
immediately before the item(s) they serve; a "predict, then confirm" item keeps its prediction
response separate from and before its confirm-the-answer response, as two numbered steps, not one.
Never print the item's answer, point value, or which strategy it is testing.

### 2.7 Speaking Task cards

For each task Level, print a plain instruction card (not a rubric): the topic in plain language,
the target length, and how/by when to submit (Teams Speaking Progress) plus the same-task
live-delivery note ("You may also do this task live in class instead - ask your teacher"). Any
"emphasizes X skill" framing from the source (B.2/B.3) gets folded into the task's own wording
(Section 1's translation row) rather than named as a measured skill. Use the star system (2.2) to
label which Level's card a student was given; do not print all four Levels' cards as a
choose-your-own menu on a single student's copy unless the teacher is distributing a
multi-Level reference sheet on purpose (flag this as a teacher decision, not this prompt's default).

### 2.8 Callout boxes, answer space, redundant rules

Same rules as the lesson packet's 2.13: callouts reserved for genuine spotlights (the citation
box), word banks get the dashed-rule exception only, answer space matched to expected answer
length, no decorative rules.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Identical to the lesson packet's Section 3: single self-contained HTML file, black-and-white only,
no em-dashes, print-safe page breaks. **Reuse `shared/Student_Packet_Style_Guide.md`'s base
stylesheet directly, plus the CSS class additions already established in the Student Print
Formatting Prompt (v1)** (`.citebox`, `.notes-table`, `.task-instr`, `.pic-options`/`.pic-option`,
`.match-list`/`.match-row`, `.qitem`) rather than inventing new ones. Add a page-break rule between
each task Level's Listening Test page (`page-break-before: always` on each Level's section) so
selective printing (2.2) produces clean single-Level printouts.

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
- Is every answer key tag, point value, holistic pass note, and rubric criterion (Not
  yet/Developing/Meets) absent from the document - not just hidden, actually removed?
- Are the two sections labeled Listening Test and Speaking Task (not "Unit," not by day)?
- Does each task Level's Listening Test material appear on its own clearly labeled page, containing
  only that Level's own items - not a four-Level choose-your-task menu?
- Does the "What You'll Listen To" citation box sit right before the Listening Notes organizer, and
  avoid inviting students to ask their teacher for the link?
- Is there a fillable Listening Notes organizer, positioned before the numbered test items, with
  wording matched to the source's real confirmed media type?
- Does every standalone question with a response line carry a number via `.qitem` or `.qlist`?
- Do multiple-choice items stay on one compact line each, with genuinely picture-based items given
  real labeled placeholder boxes and word banks placed immediately before the item(s) they serve?
- Does each Speaking Task card read as a plain instruction (topic, length, submission), with any
  skill-emphasis framing folded into the task's own wording rather than named as a measured skill,
  and the same-task live-delivery note present?
- Is the document black-and-white, em-dash-free, single self-contained HTML file, reusing the
  existing base stylesheet plus only the classes already documented for this family?
