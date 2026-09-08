# Passage Reading Student Print Formatting Prompt (v1.10)

Companion to the Passage Reading Lesson Generation Prompt (v2.8, Band-Calibrated). Takes one completed 2-day
lesson cycle and produces a single, print-ready, black-and-white student handout: one self-contained HTML
document covering both days, with every piece of teacher-facing pedagogical language translated into plain
instructions a student (or a parent glancing at the page) can act on without decoding jargon like "close reading
with annotation," "Fishbowl," or "Task Level."

**Current version: v1.9.** For the full dated version history and the reasoning behind each change, see
`Changelog.md`.

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
  Day 2 refresher text, the Collaborative Evidence Matrix's task-Level items, the discussion/oral-output content
  (2-3 prompts if the source lesson is v2.6+, one prompt if it predates v2.6 - see 2.9), and the Closing Transfer
  Check. Pull all content directly from the completed lesson; do not invent new vocabulary or tasks, and do not
  drop any task Level present in the source lesson's band.
- Module and Band, for internal reference only (they do not appear as labels in the student-facing output; see
  2.4).

### 0.2 What this prompt does NOT change

The underlying content, task Levels, and pedagogical structure are fixed by the source lesson. This prompt is a
presentation and translation layer, not a content-generation step: it does not cut or reweight comprehension
questions, does not change which task Levels exist, and does not alter the anchor text. The one narrow exception
is Section 2.9's discussion prompts when formatting a pre-v2.6 lesson that supplies only one (see 2.9) - every
other section of this prompt draws only on content already present in the source lesson. Where the source
lesson's structure genuinely does not translate to a clean print layout (see Section 1), this prompt may restructure
*presentation* (for example, merging two adjacent task-Level sections into one shared exercise with lettered
sub-items) without cutting content or changing the difficulty of any task Level's work.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

Every generated student handout must pass this translation before anything else. None of the terms in the left
column may appear in the student-facing document. Replace each with the plain-language instruction that tells
the student what to actually do, silently, without narrating the pedagogy behind it.

| Teacher-facing term (lesson prompt)                     | Student-facing translation                                                                                          |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Close Reading with Annotation                              | A short instruction plus an annotation key placed near the text, not narrated as a named strategy. As of v1.1, every packet gets this "Read & Mark It Up" treatment regardless of the source lesson's actual strategy - see 2.10. |
| Fishbowl / Town Hall / Concentric Circles / Jigsaw Expert Panels / small-group discussion carousel | A plain small-group discussion instruction: get into a group, here are your questions, take turns talking. Do not name the protocol. |
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

### 2.4 Modality/Band/Version stack, top-right; no other kicker lines or metadata fields

The document's opening masthead (the very first one - never the Unit 1B masthead) carries a
`.masthead-meta` block, alongside the `h1`, per `shared/Student_Packet_Style_Guide.md` §B: two
stacked `.masthead-tag` lines - the first reading exactly `Reading`, the second combining this
lesson's Band and its version code as one string, `<Band> <Module>.<Set>.<Lesson>.<Version>`
(e.g. `Advanced 1.1.1.0`) per `shared/Program_Conventions.md` §G. Nothing else on that stack - no
"Class" or "Packet" suffix.

Beyond that one block, do not include: a Name/Date field, a subject/module kicker line under the title
(e.g. "Reading Packet · Describing"), a subtitle line under any heading, or a footer note at the bottom of the
document. The title, its `.masthead-meta` block, and the objective statement are the only material above
"Before You Read."

### 2.5 Section and task labeling

- Use a consistent section-title style for each named block (Before You Read, Read & Mark It Up, Check Your
  Understanding, Warm-Up, Investigate the Text, Discuss It, Wrap It Up, or the equivalent set for the lesson
  being formatted).
- Within a section, label individual exercises with letters (Task A, Task B, Task C...) so the teacher can reference
  them verbally in class. Use "Task," not "Exercise."
- Where the source lesson's Day 1 comprehension items would otherwise split into two near-identical blocks
  (e.g. a Fact Finder set and a Cause & Effect set covering the same content), merge them into one combined
  Task with sequential numbered questions rather than two separate task labels, if doing so does not drop any
  content. A separate word-in-context or vocabulary completion exercise stays its own Task.
- Task labels sit inline with their instruction sentence (e.g. "Task A. Answer using the text..."), not as a
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

Translate the source lesson's oral-output protocol (Fishbowl, Town Hall, Concentric Circles, Jigsaw Expert
Panels, small-group discussion carousel) into small groups that all discuss simultaneously, not a live-rotation
format where only some students participate at a given moment. This is a print-medium constraint, not a
judgment about the live version of any protocol: a printed page is static and cannot orchestrate a timed
changeover between an inner and outer circle the way a teacher can in the room, so even a well-scaffolded live
Fishbowl or Concentric Circles (Lesson Generation Prompt v2.7, Section 0.10 - an explicit active task for every
outer-circle student, 2-3 rotated prompts) still becomes simultaneous small groups on the page.

**If the source lesson was generated under Lesson Generation Prompt v2.6 or later** (Section 0.10), it already
supplies 2-3 distinct discussion prompts - pull them directly rather than writing new ones; this is presentation
work, not content generation, matching Section 0.2. **If the source lesson predates v2.6 and supplies only one
Fishbowl-style prompt**, write 1-2 additional prompts that explore a different, related angle of the same core
question (not a rephrasing of the same question), so groups working simultaneously are not all having an
identical conversation; note in your own working notes (not on the page) that this lesson would benefit from
being regenerated or patched against the current lesson prompt so future formatting passes don't need to repeat
this step. If the source lesson used Fishbowl and supplies an outer-circle task (v2.7+), fold that task into one of
the small groups' prompts rather than dropping it, so the work it was meant to produce still happens on paper.

List prompts left-aligned, in plain regular weight (not centered, not bold, not italicized, no added quotation
marks). Provide star-coded sentence-starter phrases below the prompts, keyed to the source lesson's
differentiated stems, using the same star system as 2.6.

### 2.10 Annotation key: a standing default, not tied to one reading strategy

Every packet includes a "Read & Mark It Up" section with a floated annotation-key sidebar, regardless of which
Phase 2 reading strategy the source lesson actually used in class (Close Reading with Annotation, Teacher
Read-Aloud with Interactive Stops, Reciprocal Teaching, or any other). In print form the student reads
independently, so the interactive or oral elements of whatever strategy the classroom used (embedded stops, a
teacher's live pauses, assigned discussion roles) don't carry over; an annotation habit is what a solo reader
actually needs, and it substitutes cleanly for all of them.

Base annotation key, used on every packet:

```
underline    a word you don't know
( circle )   a connector word: but, because, when
[ bracket ]  the sentence with the paragraph's main idea
?            next to anything that surprises you
```

Add a fifth mark, `!` next to a word that feels like the writer's opinion, only when the lesson's task Levels
include an evaluative-language-spotting objective (in practice: Advanced band and up, where a native or
extension-up task Level asks students to identify evaluative word choice or an implied attitude). Do not add the
`!` mark for a Beginner/Intermediate-only lesson where no task actually asks students to find evaluative
language; an unused annotation mark is worse than no mark, since a student will look for a task that references it.

Position the key as a floated sidebar box that the article text wraps around, beside the first paragraph or two of
the anchor text, rather than as a full-width block sitting above the article.

### 2.11 Reused/refresher text blocks

Any secondary text reused from the source lesson (the Day 2 vocabulary refresher, a second comparison text
attached to a specific task) gets a plain bordered text block, visually distinct from the main anchor text but not
styled as a callout/spotlight box (reserve that treatment for genuine callouts per 2.12). Only include a rule
between the block and surrounding content where it aids readability; default to omitting it unless the block would
otherwise run into adjacent content ambiguously.

### 2.12 Callout boxes are reserved for genuine callouts

Bordered call-out containers (full border on all sides, padding, margin - the `.spotlight-box` treatment) are
reserved for content that is genuinely a spotlight moment: the idiom/slang Phrase Spotlight, and the
worked-model box in 2.7. Do not put a full border around ordinary content like a vocabulary list or a plain
instruction paragraph - those render as plain text or a simple unbordered list.

**Idioms to Know: table when there's a list, spotlight box when there's one.** A single idiom (the "Phrase
Spotlight" case) keeps the `.spotlight-box` treatment above. When the lesson glosses 2 or more idioms with no
single spotlight idiom, render them as a table using the shared `.idiom-list`/`.irow` classes (phrase, then
gloss, one row per idiom) - the same two-column treatment "Words to Know" already gets from `.vocab-list`/
`.vrow` - instead of stacked plain `.idiom-item` paragraphs. Number each row's phrase ("1. in the middle of
nowhere," "2. keep my feet on the ground," ...), restarting at 1, matching the plain "N. " prefix "Words to
Know" already uses inside its own `.word` spans. Both idiom classes and the vocabulary classes are defined in
`shared/Student_Packet_Style_Guide.md`.

**One documented exception:** a word bank (the small inline list of word-choice options accompanying a
fill-in-the-blank or star-rated task) gets a light dashed rule above and below it, distinguishing it from
surrounding prose without promoting it to a full bordered box. This is not a callout box and does not signal a
spotlight moment; it is a lighter, workbook-style convention reserved specifically for word banks, and should not
be extended to other ordinary content (a plain vocabulary list still renders with no border or rule at all).
Position a word bank immediately before the question(s) or sentence frame it actually supplies words for, not
after - a student reading top to bottom should see the options before being asked to use them.

### 2.13 Answer space

Add blank writing lines wherever a question demands a written answer, sized to the expected answer length: a
single short full-width line (e.g. `.ans-line-sm`, roughly 18px tall, beginning on its own line directly below the
question - never packed onto the same line as the question text) for a brief fact or short phrase; two or more
full-width lines (e.g. `.ans-line`, roughly 20-24px tall each) for a 2-3 sentence answer or a requested quote. Both
classes now span the full available width - `.ans-line-sm` is shorter, not narrower, than `.ans-line`. Do
not add answer space to questions with no written-response component (e.g. a fill-in-the-blank item that is
itself the answer space, or a purely discuss-aloud prompt).

### 2.14 Redundant rules and dividers

Do not add a horizontal rule between adjacent sections, headings, or blocks by default. Only include one where
it is load-bearing for readability (for example, separating a dense block of running text from a clearly distinct
block immediately below it with no other visual separation, such as a heading or box border), or where Section
2.12's word-bank exception applies. When in doubt, omit it; this program's iteration history shows decorative
rules accumulate quickly and are almost always cut on review.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

**Moved to a shared, cross-modality doc in v1.2:** paste `shared/Student_Packet_Style_Guide.md`
alongside this prompt when generating. It holds the universal format constraints (single
self-contained file, black-and-white, no em-dashes, print-safe layout), the base stylesheet, and
the HTML markup conventions - all of Section 3 for every lesson type, not just this one. This
prompt has no Reading-specific delta CSS of its own; the shared base stylesheet is the whole of
what a Passage Reading packet needs.

## SECTION 4: WORKFLOW

### 4.1 HTML preview first, iterate before finalizing

Generate the student packet as an HTML file and deliver it for review before treating it as final. Content and
task-level layout decisions in this program are still refined through direct visual review, not specified in enough
advance detail to get exactly right on the first pass, even with the base stylesheet (Section 3) now fixed. Apply feedback
as scoped, targeted edits rather than regenerating the whole document each round.

### 4.2 When this prompt's guidance runs out

Where a source lesson includes a structural element not explicitly covered above, apply Section 1's general
principle (plain instruction over jargon) and this section's general defaults (no color, no unnecessary rules,
callout boxes reserved for genuine spotlights, answer space matched to expected answer length) rather than
inventing new decorative structure, and reuse the base stylesheet's existing classes and visual language before
adding a new one.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

- Does every term in Section 1's left column appear nowhere in the student-facing text?
- Is the document a single combined packet covering every task Level in the source lesson's band, not
  separate per-task-Level handouts?
- Does the objective appear as a plain can-do statement near the top, before any task content, and does the
  closing activity connect back to that same stated objective?
- Are the two sessions labeled Unit _A / Unit _B (never "Day 1"/"Day 2"), folded into the section heading text
  itself rather than a separate divider?
- Does the opening masthead carry a `.masthead-meta` block with two stacked tags - "Reading," then this
  lesson's Band and its `<Module>.<Set>.<Lesson>.<Version>` version code combined as one string - and only there
  - never on the Unit 1B
  masthead? Beyond that block, are there no Name/Date fields, no subject/module kicker line, no subtitle
  lines, and no footer note?
- Are all exercises labeled with letters ("Task A," "Task B"...) rather than "Exercise," with labels inline with
  their instruction text?
- Do differentiated tasks show only filled stars (★ up to ★★★★), with no numeric Level, no tier name, and no
  "choose your own adventure" framing language anywhere on the page?
- Does the "share with a different-task group" instruction appear before the task list, not after, with no
  "everyone teaches everyone something" framing?
- If the objective is tested for the first time in the second session's independent tasks, is there a worked-model
  box using the actual anchor text, placed between the two sessions, stating its examples directly without
  extra framing sentences?
- Is the discussion section built as simultaneous small groups (not a live inner/outer circle format - a print-medium
  constraint, not a claim that a well-scaffolded live Fishbowl/Concentric Circles is passive), with 2-3 distinct
  prompts pulled from a v2.6+ source lesson (or authored per 2.9's fallback for an older lesson), left-aligned and
  unquoted, in regular weight, and with any outer-circle task (Fishbowl, v2.7+) folded into one of the group
  prompts rather than dropped?
- Is the annotation key present on every packet regardless of the source lesson's Phase 2 strategy, floated
  beside the first paragraph or two (not full-width above the article), with the `!` mark included only when the
  lesson's task Levels include an evaluative-language objective?
- Are callout boxes reserved for genuine spotlights (idiom/phrase spotlight, worked-model box), with word
  banks using only the light dashed-rule exception (2.12) and no other ordinary content bordered?
- Does every question requiring a written answer have appropriately sized answer space, and no answer space
  where none is needed?
- Has every decorative, non-load-bearing horizontal rule been removed, apart from the word-bank exception?
- Is the whole document black-and-white only, with no color-dependent meaning?
- Is the document free of em-dashes?
- Does the document reuse `shared/Student_Packet_Style_Guide.md`'s base stylesheet unmodified (no unrequested
  font, color, or spacing changes), with `.kicker`/`.sub` left out?
- Is the output a single self-contained HTML file with no external resource dependencies besides the print
  trigger?
