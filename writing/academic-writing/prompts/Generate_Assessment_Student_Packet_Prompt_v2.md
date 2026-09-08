# Academic Writing Assessment Student Print Formatting Prompt (v2)

Companion to `Generate_Assessment_Prompt_v2.md`. Takes one completed Set's assessment (Part A Grammar &
Mechanics Check, Part B Writing Task) and produces a single, print-ready, black-and-white student handout: one
self-contained HTML document, with every piece of teacher-facing language, and everything a student should never
see (Part A's answer keys and point values; Part B's actual rubric), removed or translated. **The one
exception:** a short self-check checklist derived from Part B's rubric Meets column appears on each Writing Task
card (Section 2.7) - not the rubric itself. Mirrors Listening/Speaking's
`Generate_Assessment_Student_Packet_Prompt_v1.md` closely - same translation principle, same one-exception
rubric-to-checklist rule - adapted for a written assessment's shape, and reuses `shared/Student_Packet_Style_Guide.md`'s
shared base stylesheet, the same one every current-convention Writing lesson packet uses
(`Generate_Student_Packet_Prompt_v2.2.md`), rather than inventing a new class family.

Use this prompt only after an Assessment `.md` already exists in full (both Part A and Part B). Do not use it to
generate assessment content, invent new items, or omit a task Level present in the Band. This produces the
**student version only**.

**Current version: v2.** For version history, see `Changelog.md`. (v2 rescopes this prompt from "one completed
lesson" to "one completed Set," matching `Generate_Assessment_Prompt_v2.md`'s own rescoping - see
`shared/Program_Conventions.md` §C. It also corrects Section 3's CSS-reuse note, which had pointed to this
modality's old pre-2026-09-08 Georgia-serif class family (`.task`/`.callout`/`table.rulebox`) - that family was
retired when this modality's lesson packets were rebuilt against the shared base stylesheet; this prompt was
never actually run, so nothing needed retrofitting, only the reference itself needed correcting. Neither this
prompt nor its companion has been run against a real Set yet.)

## SECTION 0: SCOPE AND INPUTS

Required: the completed Assessment `.md`, supplied in full - Part A's all items across every task Level, and
Part B's per-Level writing tasks and Scenario. Pull all content directly from the completed assessment; do not
invent new items, and do not drop a task Level present in the source Band.

**Never carry these into the student copy, under any heading or phrasing:** any of Part A's answer keys or
bracketed answer tags, point values or item score weights, or holistic pass-note language ("a passing
performance looks like..."). None of this is student-facing content - it is the reason this is a separate prompt
from the assessment itself rather than a formatting pass over the same document.

**The one exception: a checklist derived from Part B's rubric (B.2) Meets column** appears on that Level's own
Writing Task card - one item per criterion, phrased as something the student can check off before submitting,
using that criterion's Meets-column language reworded directly to the student where needed. The rubric's Not
yet/Developing columns and its table shape are never shown - this is a self-check checklist, not the teacher's
scoring instrument (2.7).

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

None of the left column may appear in the student-facing document.

| Teacher-facing term | Student-facing translation |
| --- | --- |
| Grammar Focus A / Focus B, Essay Focus A / Focus B (named as such) | Not named as "Focus A/B"; the grammar callout/rulebox just states the rule, the same way a lesson packet's Grammar callouts never label themselves "Focus A." |
| Task Level / Level (numeric) | A star rating (★ to ★★★★) used only to label which page a student was assigned, never a menu to choose from - an assessment is not student-choice the way a lesson's differentiated task block is. |
| Answer keys, point values, holistic pass notes (Part A only) | Never shown. Removed entirely (Section 0). |
| Rubric (B.2), Not yet/Developing/Meets criteria | Never shown as a rubric or table. Translated into a plain self-check checklist (one item per criterion, Meets-column language reworded to the student) on that Level's own Writing Task card (Section 0, 2.7). |
| "Concrete, countable content requirements" (B.1 framing) | Rephrased as a plain instruction folded into the task itself (e.g. "Include one comparison and one reason word"), never labeled as a scored requirement. |
| "New Scenario" / "transfer check" framing | Not named as such; the student simply sees the task, the same way a lesson never tells students they're being "assessed for transfer." |
| Real-world writing form / Module verb (named as such) | Not named; the task instruction states what to write plainly ("Write a paragraph comparing...") without naming the underlying form/verb. |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document, two sections

Produce a single shared document, not per-task-Level handouts, in two sections mirroring the source assessment's
two parts: a **Grammar Check** section (Part A) and a **Writing Task** section (Part B). Label them plainly as
what they are, not as "Unit" or by day - these are not taught lesson days.

### 2.2 Per-Level pages, not a differentiation menu

An assessment is not student-choice: the teacher assigns each student one task Level. Print each task Level's
Grammar Check material as its own clearly labeled page or page-break section (e.g. "Grammar Check - ★★" as a
running head), containing only that Level's own items, so a teacher can distribute (or photocopy) selectively.
Do not merge all task Levels' items into one shared choose-your-task block; here, "choose" already happened when
the teacher assigned the Level.

### 2.3 No kicker lines, no metadata fields

No Name/Date field, no Module/Band kicker, no subtitle line, no footer note - the running head from 2.2 already
shows the assigned Level.

### 2.4 Every question gets a number

Any place a student produces a specific, referenceable response gets a number, using the shared `.task-block`/
`.exercise-label` numbering pattern already established in this modality's current-convention lesson packets
(`Generate_Student_Packet_Prompt_v2.2.md`). Fill-in-the-blank items use `.ans-line-sm`; original-sentence items use
`.ans-line-sm` or `.ans-line` depending on expected length; a paragraph-editing item uses `.spotlight-box` plus a
matched number of blank `.ans-line`s for corrections, the same pattern this modality's lesson packets already use
for an editing-a-paragraph task.

### 2.5 Grammar Check items

Print that page's one assigned Level's items as plainly labeled tasks (`.task-block`/`.exercise-label`, `A.`,
`B.`, ...), in the same order as the source assessment. Every item is fill-in-the-blank, choose-the-form,
identify-sentence-type, or combine-the-sentences (the current Assessment Generation Prompt's item-format rule) -
there is no open-ended answer to size beyond the sentence level. A grammar rule table (`.rule-table`) is not
included in the assessment page itself unless the source `.md` explicitly calls for it as part of an item (this
is a check, not a re-teaching moment - do not add a Grammar callout box reviewing the rule, since that belongs to
the lesson packet, not the assessment). Never print the item's answer or point value.

### 2.6 Writing Task cards

For each task Level, print an instruction card (reusing `.spotlight-box` styling) with these parts, in order:
the Scenario in plain language; the task's concrete, countable content requirements (B.1's per-Level
requirements - these are the actual instructions, not a restated verb); the target length; blank writing space
(`.ans-line`, repeated to roughly match the target length, or a taller ruled block for essay-regime Levels); and
a short self-check checklist (`.checklist`, new class for this family - see Section 3) titled "Before you submit,
check:" - one item per that Level's rubric criterion, using its Meets-column language reworded directly to the
student. Do not print the rubric's Not yet/Developing columns or any table shape - this is a self-check list, not
the teacher's scoring instrument. Use the star system (2.2) to label which Level's card a student was given; do
not print all task Levels' cards as a choose-your-own menu on a single student's copy unless the teacher is
distributing a multi-Level reference sheet on purpose (flag this as a teacher decision, not this prompt's
default).

### 2.7 Callout boxes, answer space, redundant rules

Callouts reserved for genuine spotlights (a Writing Task card, per 2.6); word banks, where a source item uses
one, get the `.wordbank` treatment already established; answer space matched to expected answer length (a
one-word blank gets `.ans-line-sm`, a sentence gets `.ans-line`, a paragraph gets a taller ruled block); no
decorative rules.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Single self-contained HTML file, black-and-white only, no em-dashes, print-safe page breaks. **Reuse
`shared/Student_Packet_Style_Guide.md`'s base stylesheet** - the same one this modality's current-convention
lesson packets use (`Generate_Student_Packet_Prompt_v2.2.md`: `--ink`/`--paper` tokens, `.sheet`, `.masthead`,
`.spotlight-box`/`.spotlight-label`, `.task-block`/`.exercise-label`, `.rule-table`, `.wordbank`,
`.ans-line`/`.ans-line-sm`, `.print-btn`), rather than inventing a parallel system. **`.checklist` is this
family's one new delta class** (2.6): a plain list (no borders, no table shape) with a checkbox glyph
(`&#9744;`) before each item, for printing a Writing Task's self-check checklist - deliberately plainer than
`.rule-table`, since this is a student self-check list, not the teacher's scoring instrument. Add a page-break
rule between each task Level's Grammar Check page (`page-break-before: always` on each Level's section) so
selective printing (2.2)
produces clean single-Level printouts.

## SECTION 4: WORKFLOW

**Generation timing:** run this prompt immediately after an Assessment `.md` is complete, in the same
session/request - not as a separately-requested later step, the same same-session pairing rule the Lesson
Generation Prompt uses for lessons and their packets. An assessment request produces both files together: the
`.md` first, then this prompt run against that finished `.md` to produce the `.html`.

**The `.md` is the single source of truth; this prompt's output is always a regeneration, never a standalone
edited artifact.** If a review round asks for a change that affects what students actually see as an item, task,
or instruction, apply the change to the source Assessment `.md` first, then re-run this prompt to produce a
fresh `.html`. The only edits safe to apply directly to the `.html` are pure formatting/translation-layer fixes
that don't change assessment content.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

- Does every left-column term from Section 1 appear nowhere in student-facing text?
- Is every Part A answer key, point value, and holistic pass note absent from the document - not just hidden,
  actually removed (Part B's rubric is the one deliberate exception - see below)?
- Are the two sections labeled Grammar Check and Writing Task (not "Unit," not by day)?
- Does each task Level's Grammar Check material appear on its own clearly labeled page, containing only that
  Level's own items - not a multi-Level choose-your-task menu?
- Does every standalone question carry a number via the `.task-block`/`.exercise-label` pattern already established?
- Is answer space matched to expected answer length (`.ans-line-tiny` for a word, `.ans-line`/`.ans-line-sm` for
  a sentence, a taller ruled block for a paragraph)?
- Does each Writing Task card include the Scenario, concrete/countable content requirements, and target length,
  with no requirement labeled as "scored" or tied to a rubric name?
- Does each Writing Task card show a `.checklist` self-check list (one item per rubric criterion, Meets-column
  language reworded to the student) rather than the rubric's Not yet/Developing columns or a table shape?
- Does the document reuse `shared/Student_Packet_Style_Guide.md`'s base stylesheet (the same one this modality's current-convention lesson packets use), adding only
  `.checklist` as a new delta class, rather than inventing a parallel stylesheet?
- Is the document black-and-white, em-dash-free, single self-contained HTML file with print-safe page breaks?
