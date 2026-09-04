# Passage Reading Student Print Formatting Prompt (v1)

Companion to the Passage Reading Lesson Generation Prompt (v2.5, Band-Calibrated). Takes one completed 2-day
lesson cycle and produces a single, print-ready, black-and-white student handout: one self-contained HTML
document covering both days, with every piece of teacher-facing pedagogical language translated into plain
instructions a student (or a parent glancing at the page) can act on without decoding jargon like "close reading
with annotation," "Fishbowl," or "Task Level."

Use this prompt only after a lesson's Day 1 and Day 2 already exist. Do not use it to generate lesson content, and
do not use the lesson prompt to produce a student handout: the input is always an already-completed 2-day
cycle, supplied in full (both days), not a topic, Module, or Band on its own. In practice, a generation request
supplies the completed lesson directly ("format this lesson for print," with the lesson text attached or pasted in).
If no completed lesson is provided, stop and ask for it before generating anything.

This prompt produces the **student version only**. A teacher-facing formatted version (with answer keys, timing
notes, and facilitation cues layered back in) is a plausible future companion but is out of scope here; do not
attempt to serve both audiences from one output.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs before generating

- The source lesson, Day 1 and Day 2 in full: the anchor text with its paragraph lettering and footnotes, the
  Phase 1 target vocabulary and idiom/slang list, the Skill Spotlight (Section 0.8-A of the lesson prompt), the
  Day 2 refresher text, the Collaborative Evidence Matrix's task-Level items, the discussion/oral-output content,
  and the Closing Transfer Check. Pull all content directly from the completed lesson; do not invent new
  questions, vocabulary, or tasks, and do not drop any task Level present in the source lesson's band.
- Module and Band, for internal reference only (they do not appear as labels in the student-facing output; see
  2.4).

### 0.2 What this prompt does NOT change

The underlying content, task Levels, and pedagogical structure are fixed by the source lesson. This prompt is a
presentation and translation layer, not a content-generation step: it does not add, cut, or reweight comprehension
questions, does not change which task Levels exist, and does not alter the anchor text. Where the source lesson's
structure genuinely does not translate to a clean print layout (see Section 1), this prompt may restructure
*presentation* (for example, merging two adjacent task-Level sections into one shared exercise with lettered
sub-items) without cutting content or changing the difficulty of any task Level's work.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

Every generated student handout must pass this translation before anything else. None of the terms in the left
column may appear in the student-facing document. Replace each with the plain-language instruction that tells
the student what to actually do, silently, without narrating the pedagogy behind it.

| Teacher-facing term (lesson prompt)                     | Student-facing translation                                                                                          |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Close Reading with Annotation                              | A short instruction plus an annotation key (e.g. "underline words you don't know, circle connector words") placed near the text, not narrated as a named strategy. |
| Fishbowl / Town Hall / Concentric Circles / Jigsaw Expert Panels | A plain small-group discussion instruction: get into a group, here is your question, take turns talking. Do not name the protocol. |
| Task Level / Level (numeric)                                | A star rating (★ to ★★★★, more stars = more challenging), with no numeric Level shown and no tier name ("Foundation," "Extension," etc.). |
| Skill Spotlight                                            | A plain can-do objective statement near the start of the packet (see 2.2), not narrated as "today we are practicing X." |
| Closing Transfer Check                                     | A closing activity instruction (see 2.7), without naming it as a "check" or referencing assessment/evidence language. |
| K-W-L Walk / Mystery Quote / Stand Up-Move / etc.          | The plain instruction the activity produces (a warm-up question, a prompt to discuss), not the activity's name. |
| STOP & CHECK / Fact Finder / Cause & Effect set             | Ordinary numbered or lettered questions, with no internal label carried into student view. |
| Board-dependent moment                                     | Not shown to students at all; this is a teacher-facing classroom-management instruction with no student-facing artifact. |
| Foundation Support                                         | Handled per 2.8, not labeled or called out as a separate tier anywhere a student can see it. |
| Reciprocal Teaching roles (Summarizer, Questioner, etc.)   | If the source lesson uses this strategy, translate the role into a plain instruction line, not a role title with jargon attached. |

If a source lesson uses a strategy or term not listed above, apply the same principle: state the plain action the
student takes, never the pedagogical name for it.

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document, not per-task-Level handouts

Produce a single shared document covering the whole class, not separate handouts per task Level. This keeps
page numbers aligned across the room and lets the teacher reference the packet verbally ("look at Task A,
question 2") without tracking which version each student holds. Every task Level present in the source lesson's
band appears inside this one document as a self-selected star-rated option, not as a separately distributed
sheet.

### 2.2 Objective statement, stated in plain language, near the top

Immediately after the title, before any warm-up content, state the lesson's actual learning objective as a
can-do statement, not narrated as "today we're practicing..." Pull the wording from the source lesson's Skill
Spotlight and the Reading-modality objective it was built from, but phrase it as something the student can
already picture doing (for example: "describe a place by noting specific features and comparing them to
something more familiar, and identify the words a writer uses to show admiration or judgment without stating it
directly"), not as a process narration.

### 2.3 Two-part session labels, folded into section headings

Label the two sessions the lesson spans (originally Day 1 / Day 2 in the source lesson) as Unit 1A and Unit 1B, or
the equivalent numbering for the lesson being formatted (Unit 2A/2B, etc.) - never using the words "Day 1" or
"Day 2," since a teacher may not always split the two sessions across literal calendar days. Fold the label
directly into the section heading text itself (e.g., "Unit 1A: The Basilica That Refuses to Be Finished"), left-
aligned, rather than as a separate divider bar or rule. The second heading (Unit 1B) restarts its own task/exercise
lettering independently of the first; do not carry letters across the boundary.

### 2.4 No kicker lines, no metadata fields

Do not include: a Name/Date field, a subject/module/band kicker line under the title (e.g. "Reading Packet ·
Describing"), a subtitle line under any heading, or a footer note at the bottom of the document. The title and
objective statement are the only material above "Before You Read."

### 2.5 Section and task labeling

- Use a consistent section-title style for each named block (Before You Read, Read & Mark It Up, Check Your
  Understanding, Warm-Up, Investigate the Text, Discuss It, Wrap It Up, or the equivalent set for the lesson
  being formatted).
- Within a section, label individual exercises with letters (Task A, Task B, Task C...) so the teacher can reference
  them verbally in class. Use "Task," not "Exercise."
- Where the source lesson's Day 1 comprehension items would otherwise split into two near-identical blocks
  (e.g. a Fact Finder set and a vocabulary-in-context set covering the same content), merge them into one
  combined Task with sequential numbered questions rather than two separate task labels, if doing so does not
  drop any content.
- Task labels sit inline with their instruction sentence (e.g. "Task A. Answer using the text...")not as a
  separate bordered or underlined badge on its own line. Where a task's instruction is long enough that inline
  placement crowds the star rating, the instruction may break onto its own line immediately after the label and
  stars.

### 2.6 Star ratings for differentiated tasks

Where the source lesson's Collaborative Evidence Matrix or equivalent differentiated task set assigns different
task Levels, represent difficulty with a star rating instead of a Level number or tier name: the lowest task Level
in the band gets ★, and each step up the band's Task Levels row adds one star, to a maximum of ★★★★ for the
highest task Level. Show only filled stars (★, ★★, ★★★, ★★★★), never a filled-vs-empty display out of a fixed
total. Do not label the tiers ("warm-up," "solid challenge," "advanced") and do not frame the choice as "choose
your own adventure" or "pick your challenge" - state only "Investigate the Text" (or equivalent) and let the
star count speak for itself; the selection process is explained live by the teacher, not narrated on the page.

Before the star-rated tasks begin, include the instruction to share with a different-task group once finished,
positioned BEFORE the task list (not after), so a student who reads only their own chosen task does not miss it.
Do not add framing language like "everyone teaches everyone something."

### 2.7 Worked model before independent application

If the source lesson's objective is tested for the first time only in the second session's independent tasks (i.e.
nothing between Phase 1's vocabulary work and the differentiated task set actually demonstrates the skill using
the anchor text), insert a short worked-model callout box after the first session's core comprehension task and
before the second session begins. Use real sentences from the anchor text the students already read to walk
through the reasoning the objective requires (for example: naming a feature-plus-comparison sentence, then
naming a sentence where evaluative language appears, and explaining briefly why each qualifies). Label the box
with a plain, non-jargon heading such as "Focus on the Objective." State each modeled example directly; do not
add framing sentences like "here's how this works" or "the tasks ahead will ask you to do this yourself" - the
examples alone are sufficient, and the following section's tasks make the connection without it being spelled out.

### 2.8 Closing activity

Translate the source lesson's Closing Transfer Check into a plain closing instruction (Section heading: "Wrap It
Up" or equivalent) that has the student apply the exact named objective to something new, stated as directly as
possible (what to pick, what to do with it), without describing it as a check, an assessment, or referencing "what
you practiced today." If the closing activity offers different sentence-starter difficulty for different students,
present those as star-rated options in the same list style used in 2.6 and in group-discussion sentence stems
(Section 2.9), not as prose describing "a higher-star exercise."

Do not add stage directions like "say it out loud" or "your teacher may call on a few pairs to share" unless the
source lesson's mechanism specifically requires a public share step the page must instruct the student to
perform; default to omitting narration of what the teacher will do next.

### 2.9 Discussion / oral output section

Translate the source lesson's oral-output protocol (Fishbowl, Town Hall, etc.) into small groups that all discuss
simultaneously, not a format where only some students participate at a time (a whole class of realistic size,
e.g. 8-12 students, cannot be usefully split into an inner circle that talks and an outer circle that only listens).
Provide 2-3 distinct discussion prompts rather than one, so not every group in the room is discussing the
identical question at once; groups pick or rotate through them. List prompts left-aligned, in plain regular weight
(not centered, not bold, not italicized, no added quotation marks). Provide star-coded sentence-starter phrases
below the prompts, keyed to the source lesson's differentiated stems, using the same star system as 2.6.

### 2.10 Annotation key placement

Where the source lesson calls for annotation (Close Reading with Annotation or equivalent), present the
annotation key as a floated sidebar box that the article text wraps around, positioned beside the first paragraph
or two of the anchor text, rather than as a full-width block sitting above the article.

### 2.11 Reused/refresher text blocks

Any secondary text reused from the source lesson (the Day 2 vocabulary refresher, a second comparison text
attached to a specific task) gets a plain bordered text block, visually distinct from the main anchor text but not
styled as a callout/spotlight box (reserve that treatment for genuine callouts per 2.12). Only include a rule
between the block and surrounding content where it aids readability; default to omitting it unless the block would
otherwise run into adjacent content ambiguously.

### 2.12 Callout boxes are reserved for genuine callouts

Bordered call-out containers are reserved for content that is genuinely a spotlight moment: the idiom/slang
Phrase Spotlight, and the worked-model box in 2.7. Do not put a border around ordinary content like a vocabulary
list, a word bank, or a plain instruction paragraph - those render as plain text or a simple unbordered list.

### 2.13 Answer space

Add blank writing lines wherever a question demands a written answer, sized to the expected answer length: a
single short inline line (e.g. `.ans-line-sm`, roughly 300px, inline after the question) for a brief fact or short
phrase; two or more full-width lines (e.g. `.ans-line`, roughly 20-24px tall each) for a 2-3 sentence answer or a
requested quote. Do not add answer space to questions with no written-response component (e.g. a fill-in-the-
blank item that is itself the answer space, or a purely discuss-aloud prompt).

### 2.14 Redundant rules and dividers

Do not add a horizontal rule between adjacent sections, headings, or blocks by default. Only include one where
it is load-bearing for readability (for example, separating a dense block of running text from a clearly distinct
block immediately below it with no other visual separation, such as a heading or box border). When in doubt,
omit it; this program's iteration history shows decorative rules accumulate quickly and are almost always cut on
review.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

### 3.1 Single self-contained HTML file

Produce one HTML file with all CSS embedded in a `<style>` block in the head and no external resources (fonts,
scripts, images) other than a simple browser print trigger (`window.print()` on an on-screen button hidden via
`@media print`). This is what makes the document reliably printable directly from a browser without setup.

### 3.2 Black and white only

Design for black-and-white printing exclusively: no color-dependent meaning anywhere in the layout (star counts,
not color, indicate difficulty; borders and typographic weight, not color, distinguish content types). Use a pure
black/white/gray palette.

### 3.3 No em-dashes

Never use em-dashes anywhere in the generated document. Use standard hyphens, colons, or parentheses
instead, consistent with the lesson generation prompt's own constraint.

### 3.4 Print-safe layout

Use `page-break-inside:avoid` / `break-inside:avoid` (or the modern equivalent) on content blocks that should not
split awkwardly across a printed page: callout boxes, task blocks, individual questions with their answer lines,
and reused/refresher text blocks.

## SECTION 4: WORKFLOW

### 4.1 HTML preview first, iterate before finalizing

Generate the student packet as an HTML file and deliver it for review before treating it as final. Layout and
formatting decisions in this program are refined through direct visual review, not specified in enough advance
detail to get exactly right on the first pass. Apply feedback as scoped, targeted edits rather than regenerating
the whole document each round.

### 4.2 When this prompt's guidance runs out

Where a source lesson includes a structural element not explicitly covered above, apply Section 1's general
principle (plain instruction over jargon) and this section's general defaults (no color, no unnecessary rules,
callout boxes reserved for genuine spotlights, answer space matched to expected answer length) rather than
inventing new decorative structure.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

- Does every term in Section 1's left column appear nowhere in the student-facing text?
- Is the document a single combined packet covering every task Level in the source lesson's band, not
  separate per-task-Level handouts?
- Does the objective appear as a plain can-do statement near the top, before any task content, and does the
  closing activity connect back to that same stated objective?
- Are the two sessions labeled Unit _A / Unit _B (never "Day 1"/"Day 2"), folded into the section heading text
  itself rather than a separate divider?
- Are there no Name/Date fields, no module/band kicker line, no subtitle lines, and no footer note?
- Are all exercises labeled with letters ("Task A," "Task B"...) rather than "Exercise," with labels inline with
  their instruction text?
- Do differentiated tasks show only filled stars (★ up to ★★★★), with no numeric Level, no tier name, and no
  "choose your own adventure" framing language anywhere on the page?
- Does the "share with a different-task group" instruction appear before the task list, not after, with no
  "everyone teaches everyone something" framing?
- If the objective is tested for the first time in the second session's independent tasks, is there a worked-model
  box using the actual anchor text, placed between the two sessions, stating its examples directly without
  extra framing sentences?
- Is the discussion section built as simultaneous small groups (not an inner/outer circle format), with 2-3
  distinct prompts, left-aligned and unquoted, in regular weight?
- Is the annotation key (if used) a floated sidebar next to the first paragraph or two, not a full-width block
  above the article?
- Are callout boxes reserved for genuine spotlights (idiom/phrase spotlight, worked-model box) and not used for
  ordinary content like vocabulary lists or word banks?
- Does every question requiring a written answer have appropriately sized answer space, and no answer space
  where none is needed?
- Has every decorative, non-load-bearing horizontal rule been removed?
- Is the whole document black-and-white only, with no color-dependent meaning?
- Is the document free of em-dashes?
- Is the output a single self-contained HTML file with no external resource dependencies besides the print
  trigger?
